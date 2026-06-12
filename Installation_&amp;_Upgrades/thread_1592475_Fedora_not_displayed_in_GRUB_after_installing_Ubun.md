---
title: "Fedora not displayed in GRUB after installing Ubuntu"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by egrar on 2010-10-10
Got Ubuntu 10.10 amd64 installed.. I've been using Fedora 13 64bit for some time now dual boot with WinXP..  Ubuntu installation to a free Hard drive went well till i rebooted, my Fedora installation was gone
, and i thought Ubuntu is much installer friendly than fedora.. need help here. thanks.

---

### Post by oldfred on 2010-10-10
Ubuntu used to have the advanced button but I think they have a combo box now that asks where to install grub2. You must have installed grub by default to your sda when you reallly wanted it in sdb?

Reinstalling Fedora's grub is probably the same but I do not know for sure.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Ubuntu should find your Fedora install. If it has not, run
 sudo update-grub

If booted you can just install grub2 to sdb with:

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

