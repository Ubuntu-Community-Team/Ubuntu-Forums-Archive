---
title: "USB Drive Reported as sda, GRUB installing on that instead of HDD"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by scooter0 on 2010-06-25
I'm trying to install Ubuntu 10.04 on my netbook, so I made a bootable USB drive and it booted fine, installed ok from that.  But now my computer will only boot to Ubuntu if the USB drive is plugged in.  GRUB was installed on /dev/sda which is the USB drive and I am not sure of the exact commands to get GRUB properly on /dev/sdb.

I tried setting /dev/sdb1 as bootable in gparted and running grub-install /dev/sdb, but that just left me with a grub command line at boot time, and I could figure out how to get into Ubuntu from there.


I also tried reinstalling with the alternate ISO, thinking maybe the text based installer would give me more of a chance to specify not to install GRUB on /dev/sda, but alas that did not work.  What's worse, is that the proprietary drivers for my Broadcom chipset installed fine the first time around, but with this new install, the Hardware Drivers utility says it finds no hardware with proprietary drivers and I cannot seem to get my wireless to work.

Thanks in advance!

---

### Post by oldfred on 2010-06-26
Welcome to the forums.

Installing grub to the USB that you used for installing now has messed it up, but if you can boot to your new install. Once you have booted is the USB still sda or has it switched. You may still need to install to sda??

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
Find which drive has the ext3 or ext4 partition - sda or sdb?

if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

this will get it to save the correct drive to install to.
sudo dpkg-reconfigure grub-pc


Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by scooter0 on 2010-06-26
When booting with the USB drive plugged in, it boots to the install on my internal hard drive.  The USB drive is /dev/sda and /dev/sda1 is mounted as /media/E241-E463 and the internal hard drive is /dev/sdb and /dev/sdb1 is mounted as /.

---

### Post by scooter0 on 2010-06-26
Thanks for the advice, oldfred, it worked.  Here are the commands I ran were:

sudo grub-install /dev/sdb
sudo update-grub
sudo grub-install --recheck /dev/sdb

Then set /dev/sdb1 with a boot flag in gparted.  Boots ok now.

And thanks for the welcome!

---

### Post by oldfred on 2010-06-26
Glad you got it working. You figured out that it is sdb not sda.

You should run this:
sudo dpkg-reconfigure grub-pc

That saves a sdb setting so reinstalls will go there. Of course if you move disks around and it is not sdb it will still install to sdb which may not be correct. Normally it just defaults to sda which may or may not be correct also.

---

