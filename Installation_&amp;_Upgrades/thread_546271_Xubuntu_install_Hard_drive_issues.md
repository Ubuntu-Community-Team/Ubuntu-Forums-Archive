---
title: "Xubuntu install Hard drive issues"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by mac0s9user on 2007-09-08
I am trying to install Xubuntu on a friends hard drive as win XP was crashing and had multiple registry problems. I am currently running the memory test (from the live CD) and it is showing a lot of errors. When I try to install xubuntu via Live CD IT says that permissions have been denied. I try to manually edit the partition scheme and get the same error. I tried regular ubuntu and it wont even load the install screen. Any Ideas? Feel free to IM at mac0s9user   (thats a zero) on yahoo/AIM


*Edit*

 I forgot the system specs.

1.5 Ghz Intel Celeron Toshiba Laptop (with a SCSI Hard drive no less)

---

### Post by Pumalite on 2007-09-08
Make sure you have a system in working order first. Then use Gparted, make one large partition formatted ext3, then install using Guided>Use Entire Disk
Do md5sum on iso
Burn at 4x
Check for CD Corruption before install

---

### Post by mac0s9user on 2007-09-08
Thanks for the reply. I did as you said. Checked the CD and it was okay (I burned it at 8x as my CD rom wont go any slower)

When I go to Gparted and try to partition it I receive the following error:

Create new file system
mkfs.ext3 /dev/sda1
mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted; will not make a file system here


When I select okay it goes back to Gparted and the partition is now locked and the file system is unknown  With a ! next to it. When I select more information I get the following errors:

Unable to detect file system.

Thanks again for your help .I am trying to make this as detailed as possible.


I can erase the partition but I cant make a new one

---

### Post by Pumalite on 2007-09-08
That's because you are using Gparted from Live CD. You need this Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (stand alone, burn to CD, bootable program)

---

### Post by mac0s9user on 2007-09-08
I have downloaded the stand alone Gparted. Is there a specific scheme I should use? I tried auto and it seems to stop at "Detecting Adaptec I20 RAID controllers" Does this section normally take a while?

---

### Post by Pumalite on 2007-09-08
You have to download the iso. Burn it as 'Image' to a CD. And then boot from that CD. AT the boot prompt; hit 'Enter'

---

### Post by mac0s9user on 2007-09-08
When I hit enter I get this screen  [http://www.urlimg.com/img.php?img=bbecaabef.jpg](http://www.urlimg.com/img.php?img=bbecaabef.jpg)

if I select auto-config it runs but stall at this section

[http://www.urlimg.com/img.php?img=cefffcadc.jpg](http://www.urlimg.com/img.php?img=cefffcadc.jpg)

---

### Post by Pumalite on 2007-09-08
You have trouble with your hardware. You better remember your specs.

---

### Post by mac0s9user on 2007-09-08
What do you suggest I do? Am I up a creek without a paddle? Thanks again for your help I do appreciate it

---

### Post by Pumalite on 2007-09-08
Try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
It has a partitioner too.

---

### Post by mac0s9user on 2007-09-08
Well I did Rescue CD as well as download the text based installer of xubuntu.  Everything worked! I am on it right now. Thanks you very much pumalite

---

