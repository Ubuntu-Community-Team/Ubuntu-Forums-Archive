---
title: "Installed versions 12.04 and 12.10 (dual boot setup), want to uninstall 12.10"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by RyanJA1982 on 2013-08-30
Hi all! The title pretty much says it all. I'd like to uninstall version 12.10 while leaving 12.04 intact. I've done a bit of searching, and couldn't find an easy answer unfortunately (the googles, they do nothing!). Any help on this? Gracias, and hope you guys have an awesome long weekend!

---

### Post by oldfred on 2013-08-30
Boot into 12.04 and install its grub2 boot loader into the MBR.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

   #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then you can delete or reuse the partition that 12.10 is installed into.

Also:
      
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by RyanJA1982 on 2013-08-30
Much appreciated! Thanks!

---

