---
title: "Can I have /boot on BTRFS?"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by martin30002 on 2016-10-03
I have ubuntu 16.04 running on BTRFS, but since some pages said that GRUB2 (2.02-beta2) cannot boot from BTRFS, I made a boot partition in ext4 for /boot.
But this partition is too small, only 150MB.
Can I put /boot onto BTRFS and how can I test it without making my system unbootable?

[COLOR=#111111][FONT=Ubuntu]How does the system find my ext4 boot partition and mount it to /boot?
[/FONT][/COLOR]
Is it possible to create a /boot2 directory in btrfs, copy the files from /boot into it and change /boot/grub/grub.cfg by adding a new menu entry saying "boot from /boot2"?

This is now how I plan it:

> #create copy of boot areacd /boot
sudo tar cfv /xboot.tar *
sudo mkdir /boot2
cd /boot2
sudo tar xf /xboot.tar
sudo rm /xboot.tar


#rename
mv /boot /boot-old
mv /boot2 /boot


#new grub install
sudo grub-install /dev/sdb5 ????
sudo debconf-show grub-pc
sudo dpkg-reconfigure grub-pc


---

