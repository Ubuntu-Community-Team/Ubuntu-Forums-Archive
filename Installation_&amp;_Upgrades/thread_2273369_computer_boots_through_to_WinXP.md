---
title: "computer boots through to WinXP"
date: 2015-04-12
forum: Installation &amp; Upgrades
---

### Post by Sherman_Willden on 2015-04-12
I have WinXp without Service Pack 2. I am trying to replace WinXP with Ubuntu. I used Ubuntu 3.13.0-48-generic and Brassaro to burn xutuntu i386 to CD. The CD has everything on it I think. The disk contents are listed below. I have the boot sequence on the WinXP machine with CD first then hard drive then removable. 

I boot the WinXP machine with the CD in. The machine's disk light is lit and I hear sounds like the machine is trying to do something with the CD. After awhile the machine boots to WinXP bypassing the CD. 

If you need more information please let me know.

Thank you in advance;

Sherman

Xubuntu 14.10 i386
sherman: cd X*
sherman: ls
boot    dists    isolinux    pics  preseed             ubuntu
casper  install  md5sum.txt  pool  README.diskdefines
sherman: ls -l
total 37
dr-xr-xr-x 1 sherman sherman  2048 Oct 22 13:47 boot
dr-xr-xr-x 1 sherman sherman  2048 Oct 22 13:47 casper
dr-xr-xr-x 1 sherman sherman  2048 Oct 22 13:47 dists
dr-xr-xr-x 1 sherman sherman  2048 Oct 22 13:47 install
dr-xr-xr-x 1 sherman sherman 18432 Oct 22 13:47 isolinux
-r--r--r-- 1 sherman sherman  3605 Oct 22 13:47 md5sum.txt
dr-xr-xr-x 1 sherman sherman  2048 Oct 22 13:47 pics
dr-xr-xr-x 1 sherman sherman  2048 Oct 22 13:47 pool
dr-xr-xr-x 1 sherman sherman  2048 Oct 22 13:47 preseed
-r--r--r-- 1 sherman sherman   226 Oct 22 13:47 README.diskdefines
lr-xr-xr-x 1 sherman sherman     1 Oct 22 13:47 ubuntu -> .

---

### Post by user_of_gnomes on 2015-04-12
Hi Sherman, 

Is the DVD-player defective perhaps? How did you create the bootable dvd?

---

### Post by Sherman_Willden on 2015-04-12
I started 2003 Knopix from the CD and that went well. I get a blank screen during the boot from the xubuntu cd until it boots into WinXP. When I view the CD from my Ubuntu host I see the files as I listed them earlier. When I try to view the xubuntu files after the WinXP boots I don't see any files but the properties show the CD is 100% used.

Thank you;

Sherman

---

### Post by yancek on 2015-04-12
You are not actually using a CD are you?  The Xubuntu downloads are all too large to fit on a CD.  The files you show on the CD/DVD look correct.  If it is booting through to xp, then I expect the changes you made to set the CD/DVD drive to first boot priority in the BIOS are not being saved.  That or the drive might be dirty or failing, the iso might have been corrupted or the burn to DVD was bad.

---

### Post by user_of_gnomes on 2015-04-13
Did you try removing the hard drive from the boot order entirely? Sometimes those CD's/DVD's need a little more time to boot but I suspect a mechanical defect as well.

---

