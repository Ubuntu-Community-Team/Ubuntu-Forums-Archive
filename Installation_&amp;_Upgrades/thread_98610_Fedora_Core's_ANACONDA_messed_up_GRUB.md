---
title: "Fedora Core's ANACONDA messed up GRUB"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by Fearan on 2005-12-03
I tried to make my computer a triple boot with Ubuntu Breezy (long standing installation, works fine!), Fedora Core 4 (new) and Windows 98 (...).  I used to have a dual-boot between Ubuntu, on a reiserfs, and Win98, on a fat32, which worked decently, until i decided to install Fedora Core 4.  I resized the win98 partition with gparted to make room for it, and it worked.  I then downloaded and burned all 4 fedora core installation CD's.  This worked.  I then installed Fedora Core on the empty space with Anaconda (came on the FC4 cd) and it messed up my GRUB Bootloader.  It seems to have installed another one on its own partition, which I chose, but when I boot up into FC4, something peculiar stops it from going further.  My partitions are as follows:
```
/dev/hda1 - (hd0,0) - vfat     - Windows 98 SE
/dev/hda2 - (hd0,1) - reiserfs - Ubuntu Breezy
/dev/hda3 - extended[INDENT]/dev/hda5 - swap[/INDENT]/dev/hda4 - (hd0,3) - ext3 - FC4
```
1: When FC4 boots up, it recognizes that the kernel and initrd are on /dev/hda4 (hd0,3), which is correct.  However, later in the bootup, fsck tries to check /dev/hda2 (hd0,1) and comes up with an error that the ext3 superblock is bad, which it is, because it's reiserfs, not ext3.  I found that the problem is that it is looking for the partition labeled "/", of which there are two: /dev/hda2 (hd0,1) and /dev/hda4 (hd0,3).  It then brings me to a login in which I am allowed to do anything I need to correct this problem, however, the filesystem is mounted as /dev/root on / (ro).  This created a problem, as now i can't edit fstab to try to remedy the problem.  How would I get fsck to check /dev/hda4 (hd0,3) instead, which is what it should be doing? :confused: 

2: In the FC4 installation of GRUB, I have lost the GRUB kernel and initrd lines for Ubuntu Breezy.  Instead, it is something like this:
```
rootnoverify (hd0,1)
chainloader +1
```
Any help on what options I should enter into the GRUB menu.lst when I can access it?

Thanks a bunch,
Fearan

---

### Post by bwog on 2005-12-03
You can restore grub in the rescue mode of the ubuntu install disk: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

Perhaps you have to add fedora later.

---

### Post by Fearan on 2005-12-03
[QUOTE=bwog]You can restore grub in the rescue mode of the ubuntu install disk: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

Perhaps you have to add fedora later.[/QUOTE]
Thanks, I will do this as soon as i can get to my computer

---

### Post by Fearan on 2005-12-07
Thanks... i used your help, and i am now in ubuntu! now to figure out what to do with fedora core...

---

### Post by bwog on 2005-12-07
You have to edit grubs menu.lst.

sudo gedit /boot/grub/menu.lst

below the line ### END DEBIAN AUTOMAGIC KERNELS LIST there should be a title for fedora, below is just an example I found

title Fedora Core (2.6.11-1.27_FC3)
	root (hd1,0)
	kernel /boot/vmlinuz-2.6.11-1.27_FC3 ro root=LABEL=/1 rhgb quiet
	initrd /boot/initrd-2.6.11-1.27_FC3.img
title Fedora Core (2.6.9-1.667)
	root (hd1,0)
	kernel /boot/vmlinuz-2.6.9-1.667 ro root=LABEL=/1 rhgb quiet
	initrd /boot/initrd-2.6.9-1.667.img

you may have a different version, on another partition, and other bootparameters

Edit: Note that grub starts counting from zero for hard disks and partitions

Edit: typo; edit changed in gedit (you can use nano instead of gedit, like Azz suggests below, but edit was wrong, so thanks for pointing that out)

---

### Post by az on 2005-12-07
You rock!  Very helpful.  

[QUOTE=bwog]You have to edit grubs menu.list.

sudo edit /boot/grub/menu.lst
[/QUOTE]

The only thing is that edit will not work.  You can use nano or vi:

sudo nano /boot/grub/menu.lst

---

