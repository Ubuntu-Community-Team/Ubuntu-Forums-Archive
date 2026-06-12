---
title: "Backup prior or rewrite MBR after Windows re-installation"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by pi6502 on 2014-03-16
Hi,

I am running a dual system  having two drives: W7 64 bit PE on the hdd and ubuntu 12.04 LTS on the sdd. GRUB is installed on first boot drive, the hdd.

I need to reinstall W7 64 bit (doh!) and this will overwrite hdd and mbr of course. Now what would be best to do and how?

- Backup the MBR and restore it after W7 reinstallation?
- Use a CD/DVD to boot ubuntu 12.04 and restore grub from within the installation?

Thanks for caring!

---

### Post by oldfred on 2014-03-16
Just boot into Ubuntu and install grub to sdd's MBR. Check that you can boot from sdd in BIOS.

When installing Windows be sure that BIOS is set to boot from sda, as Windows also installs its boot loader 100MB partition to the drive set to boot in WIndows. If you leave it at sdd, it overwrites the first 100MB as it does not see Linux partition and can make a mess of things. Good backups always best.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Grub also remembers the drive it orginally installed to. Best to check and change to sdd drive. Otherwise an update may update sda, when you want sdd updated.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

