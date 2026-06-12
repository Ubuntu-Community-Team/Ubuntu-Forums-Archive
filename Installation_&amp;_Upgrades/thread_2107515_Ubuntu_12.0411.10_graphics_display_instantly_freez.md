---
title: "Ubuntu 12.04/11.10 graphics display instantly freezes"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by TheRealSuperman on 2013-01-22
Hello,

I am trying to install Ubuntu 12.04.1 LTS or 11.10 (64bit versions). I have a Geforce 580GTX graphics card. When I just install the system normally and boot it up it will freeze almost instantly at the login screen. Sometimes I manage to push F2+Alt+Ctrl in time and can read "GPU Lockup - switching to software fbcon". I am aware this is a known problem and I have tried a lot of the suggested solutions.

I tried removing the nouveau driver and installing the nvidia drivers by:
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get install linux-headers-`uname -r`
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo ldconfig
sudo update-initramfs -u
sudo nvidia-xconfig

did not work... The graphics would freeze again.

I then reinstalled Ubuntu and tried installing the Nvidia driver manually using the NVIDIA installer (version 295.49), which also did not help.

I tried installing Ubuntu by checking the 'nomodeset' option in the installation menu... well this also did not work...

I could install Ubuntu 10.10 without problems, but I would really prefer using a newer version.

Any ideas want I can do to get one of the newer versions installed preferably 12.04.1 LTS?

Thank you!

---

### Post by Allister93 on 2013-03-06
Had the exact same problem with the geforce 590gtx, seems to be a common  problem but so many different fixes, like you i tried heaps of them in  the end this worked for me

sudo apt-get install linux-headers-generic
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot


Good luck, hope it works for you too.

---

