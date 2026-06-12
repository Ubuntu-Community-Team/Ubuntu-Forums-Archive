---
title: "Dual boot Ubuntu 16.04 and Fedora"
date: 2017-03-15
forum: Installation &amp; Upgrades
---

### Post by Music_Guy on 2017-03-15
I know this has been discussed before, though several of the discussions are older. I just want to get a sanity check before I start.

I have a MacPro currently running Ubuntu Studio 16.04. It is installed on a 1 Tb hard drive, using the standard Ubuntu setup during installation (ie. boot sector, swap sector, and Ubuntu). Currently Ubuntu is actually using about 150 Gb of disk space. I want to set up this machine to dual boot with Ubuntu and Fedora. This is my plan:
- Use GParted to resize the Ubuntu partition to about 500 Gb.
- Set up the remaining space (~450 Gb) as ext4.
- Install Fedora on the 450 Gb partition, as an LVM installation
- Go back to Ubuntu and execute the following commands:
   
# to find an LVM install from a non-LVM install
sudo apt-get install lvm2
sudo vgchange -a y
sudo update-grub
(from: [http://askubuntu.com/questions/854215/dual-booting-regular-ubuntu-with-lvm-fedora/854216](http://askubuntu.com/questions/854215/dual-booting-regular-ubuntu-with-lvm-fedora/854216)
with a fallback on: [https://ubuntuforums.org/showthread.php?t=2312703&highlight=fedora](https://ubuntuforums.org/showthread.php?t=2312703&highlight=fedora))

It's my understanding that this process will allow me to dual boot.
Is there anything that I missed? Do I have to modify grub to give me time to select which OS I want to boot?

Thanks.   :?:

---

### Post by Dennis N on 2017-03-15
Since you are installing Fedora after Ubuntu, Fedora will place itself first in boot order, and would be the OS whose grub menu you see on start up. 

For BIOS installs:
If you wanted to boot Ubuntu's grub on start up, you need to boot into Ubuntu and install grub and then update it. Also be sure lvm2 is installed.

For UEFI installs:
If you wanted to boot Ubuntu's grub on start up, you use efibootmgr and change the boot order to put Ubuntu first.

Note: if you boot to Ubuntu's grub initially, and your OSes are installed in UEFI mode, Ubuntu's grub will not boot Fedora without making some changes. At least, that was my experience in the past, but maybe that has been corrected now.

---

### Post by Music_Guy on 2017-03-15
Thanks @Dennis. From what I've read Fedora will install in UEFI mode. I was not aware that there was an efibootmgr. I'll read about that before I plow ahead.

---

