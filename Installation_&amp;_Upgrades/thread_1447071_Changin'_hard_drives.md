---
title: "Changin' hard drives"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by astro4travel on 2010-04-04
Hi,
I have my failing C:drive with Windows XP on it. On my second hard drive, I have Ubuntu Karmic installed. Now, my question is that I have to reinstall Windows after I replace my 1st. hard drive. Will this affect the Grub boot loader from appearing after I have XP reinstalled and go to reboot? Hope this is clear. Thanks in advance. Michael

---

### Post by 2hot6ft2 on 2010-04-04
> **astro4travel said:**
> Hi,
I have my failing C:drive with Windows XP on it. On my second hard drive, I have Ubuntu Karmic installed. Now, my question is that I have to reinstall Windows after I replace my 1st. hard drive. Will this affect the Grub boot loader from appearing after I have XP reinstalled and go to reboot? Hope this is clear. Thanks in advance. Michael
If the windows drive is the first in the boot order in the BIOS which it usually is (windows doesn't like being anywhere else) then yes.

Before you do it make sure of the size and location of your Kubuntu.
After installing windows it will only boot windows so you'll need to reinstall grub 2 like this (just imagine it says Kubuntu where it says ubuntu)

Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
```
To find out you partitions run
```
fdisk -l
```
Use that info for the following
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```

---

