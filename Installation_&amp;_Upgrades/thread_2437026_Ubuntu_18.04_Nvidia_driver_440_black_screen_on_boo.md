---
title: "Ubuntu 18.04 Nvidia driver 440 black screen on boot."
date: 2020-02-17
forum: Installation &amp; Upgrades
---

### Post by mtbdrew on 2020-02-17
This occurred at initial install and re-occurs every time there is a kernel update.  Each time I have to repeat these steps in order to get working desktop environment:

[https://askubuntu.com/questions/1129516/black-screen-at-boot-after-nvidia-driver-installation-on-ubuntu-18-04-2-lts](https://askubuntu.com/questions/1129516/black-screen-at-boot-after-nvidia-driver-installation-on-ubuntu-18-04-2-lts)

sudo apt-get update

sudo apt-get upgrade

sudo apt-get remove nvidia*

sudo apt autoremove

sudo apt-get install dkms build-essential linux-headers-$(uname -r)

echo "# Disable the default Nouveau kernel driver" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf

echo "# -----------------------------------------" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf

echo "blacklist nouveau" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf

echo "blacklist lbm-nouveau" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf

echo "options nouveau modeset=0" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf

echo "alias nouveau off" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf

echo "alias lbm-nouveau off" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf

cat /etc/modprobe.d/blacklist-nouveau.conf

echo "options nouveau modeset=0" | sudo tee -a /etc/modprobe.d/nouveau-kms.conf

cat /etc/modprobe.d/nouveau-kms.conf

sudo update-initramfs -u

sudo service lightdm stop

sudo apt-get install nvidia-driver-440

lsmod | grep nvidia

sudo lshw -c video | grep 'configuration'

---

### Post by oldrocker99 on 2020-02-17
This should fix things:
```
sudo apt install dkms
```

I don't know if you'll need to deinstall and reinstall the nVidia driver, but dkms stands for Dynamic Kernel Module Support. It will automagically connect the nVidia driver to the new kernel.

---

### Post by mtbdrew on 2020-02-17
it is already installed and the latest version:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.7).
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.


I have done the steps detailed in [https://askubuntu.com/questions/1129...tu-18-04-2-lts](https://askubuntu.com/questions/1129...tu-18-04-2-lts) since installing dkms and still have to re-do them every time the kernel is updated.

---

### Post by mastablasta on 2020-02-18
is kernel the latest one now?

is the output maybe going to some other exit on the GPU card? i have older chip and sometimes output would land on TV instead of on the monitor.

---

### Post by mtbdrew on 2020-03-18
System is totally up to date. No other outputs on this card.

Update, the issue did not occur after last system update. However the situation did arise when system boot with the TV turned off. Had to redo all the steps here ([https://askubuntu.com/questions/1129...tu-18-04-2-lts](https://askubuntu.com/questions/1129...tu-18-04-2-lts)) to get screen working again.

---

### Post by mtbdrew on 2020-04-07
Issue happened again after latest kernel update when doing the autoremove to clean up.

---

### Post by mastablasta on 2020-04-09
1. what is your GPU?
2. have you entered purge command?
```
[COLOR=#242729][FONT=Consolas]sudo apt-get purge nvidia*[/FONT][/COLOR]
```
3. what are correct drivers for your GPU? 440 ?
4. have you tried 20.04 (beta, but soon to be released new LTS with new kernel)?

---

### Post by mtbdrew on 2020-04-29
Yes I have done the purge as well. No I have not tried 20.04 why would I they haven't fixed this in the last two releases so what makes you think the next will work?

GPU is Nvidia Geforce GT-630 using 440 driver.

---

### Post by CelticWarrior on 2020-04-29
> **mtbdrew said:**
> Yes I have done the purge as well. No I have not tried 20.04 why would I they haven't fixed this in the last two releases so what makes you think the next will work?

GPU is Nvidia Geforce GT-630 using 440 driver.

What would they need to fix exactly? This seems to be a unique problem affecting your system.
I have been managing for years 4 PCs with the same card, running 18.04 with the latest Nvidia drivers without issues. Previously they were running 16.04, no problems at all.

---

### Post by mastablasta on 2020-04-30
I don't think GT630 supports 440 driver. in fact i think the latest one is 390.xx series and this chip moved to legacy. mine will also go soon if it's not there already. :-/

edit - more info: [https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)

---

### Post by CelticWarrior on 2020-04-30
> **mastablasta said:**
> I don't think GT630 supports 440 driver. in fact i think the latest one is 390.xx series and this chip moved to legacy. mine will also go soon if it's not there already. :-/

edit - more info: [https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)

It does support 440 according to Nvidia and no, not yet legacy but I'm sure it'll be sooner than later.

---

