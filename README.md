# fastsetup
> Setup all the things

First, do basic ubuntu configuration, such as updating packages, and turning on auto-updates:

```
sudo apt update && sudo apt -y install git
git clone https://github.com/sabrinagannon/fastsetup.git
cd fastsetup
sudo ./ubuntu-initial.sh
# wait a couple of minutes for reboot, then ssh back in
# If you're using WSL (Windows) use `sudo ./ubuntu-wsl.sh` instead of the above line
```

Then, optionally, set up [dotfiles](https://github.com/fastai/dotfiles):

    source dotfiles.sh

...and set up conda:

```
source setup-conda.sh
. ~/.bashrc
conda install -yq mamba
```

To set up email:

    sudo ./opensmtpd-install.sh

To test email, create a text file `msg` containing a message to send, then send it with:

    cat msg |  mail -r "x@$(hostname -d)" -s 'subject' EMAIL_ADDR

Replace `EMAIL_ADDR` with an address to send to. You can get a useful testing address from [mail-tester](https://www.mail-tester.com/).

## NVIDIA drivers

To install NVIDIA drivers, if required:

```
ubuntu-drivers devices
sudo apt-fast install -y nvidia-XXX{-server}
sudo modprobe nvidia
nvidia-smi
```
