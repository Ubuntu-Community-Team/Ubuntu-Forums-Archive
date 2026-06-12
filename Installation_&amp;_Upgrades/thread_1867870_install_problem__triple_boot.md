---
title: "install problem  triple boot"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by tronnix75 on 2011-10-23
here is my scenario, i have tried numerous FAQ's, posts and blogs about this installation and it has worked in the past but not now.  i am trying to triple boot with Xp, windows 7 and ubuntu.  I have windows xp pro, windows 7 ultimate and ubuntu version 10.10.  my rig is setup as follows:

Asus P5n -e sli MB
intel dual core E6600
4gb of ram
Nvidia 8800gts video card
creative 7.1 SB card

hard drive:
first hard drive is 280gb I installed Windows xp first on this drive
two hard drives configured as stripe raid 800gb installed Windows 7 on this pair of drives

I then created a partition using Windows 7 of 30gig for ubunutu. I formated the drive as Ntfs like some others said to do?

I then run Wubi does not after reboot it says it can not find installation files so i start over and delete the partition format it then boot from the ubuntu cd 10.10 and do a install from there still does not work.  Windows 7 bootloader does not see the ubuntu installation on the 30gig drive. is the install confused about the drives.  what is the issue. please help. :confused:

---

### Post by oldfred on 2011-10-23
Wubi may be confused about whether is is updating boot.ini for XP or BCD for Windows 7.

I do not know wubi, but one of its main advantages is not having to create another partition. (new users do not understand partitions and want to easily uninstall). So if creating a partition, why not do a full partition install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can use gparted on the non-RAID drive to create a ext4 partition and a small swap partition as a standard dual boot.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

