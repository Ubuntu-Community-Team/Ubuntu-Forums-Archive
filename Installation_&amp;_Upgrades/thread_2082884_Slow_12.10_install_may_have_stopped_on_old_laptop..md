---
title: "Slow 12.10 install may have stopped on old laptop."
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by rs2k on 2012-11-10
As a fun project, I've been installing lubuntu 12.10 using unetbootin and a usb stick on an old laptop (PII 333, 128 MB RAM) with no floppy, cd-rom drive or bootable usb feature for the last several hours. It's been going very slow. Fer the last hour and a half it's been stuck at "in-target: Building dependency tree..." during the "Select and install software" stage of the installation. Going into the second console and running "free" every so often, I can see that there is some memory and swap usage going on, but nothing seems to be changing when I run the "df" command. 

To get the install to work I used unetbootin to boot off of the disk drive and start the install. Once I got that going I ran the following commands (sdc1 is the usb flash drive):

umount /cdrom
mount -t vfat /dev/sdc1 /mnt/usb
mount -t iso9660 -o loop /mnt/usb/lubuntu-12.10-alternate-i386.iso /cdrom

I was then able to partition and format the c drive and installation had been going fine up to the point when it started to build the dependency tree. I was even able to get the usb wifi adapter to work. I choose OpenSSH Server and Lubuntu Desktop options for package installs if it makes a difference.

At what point does the boot loader get installed? I'm afraid to restart this thing since I won't have any means of booting if there is no loader installed. Any ideas?


**UPDATE: Almost 2 hours later and the next step is happening: "Reading State Information" lol**

---

### Post by Bucky Ball on 2012-11-10
Yea, there's no chance of getting Ubuntu to work on a machine with 128Mb of RAM and even though Lubuntu says it will, that's very doubtful, too.  ;)

From their website:

> We have done many tests and we found out that Lubuntu  can be installed on a Pentium II or Celeron system with 128 MB of RAM, *_ but such a system would not perform well enough for daily use.  _*
With 256MB - 384MB of RAM, the performance will be better and the system will be more usable. 
With 512MB of RAM, you don't need to worry much. 

They mention they've achieved an install with 128Mb RAM but don't explain what hoops they may have jumped through to get there. Gold star for your efforts so far and another if you can get this up, but don't like you chances ... good luck.

---

### Post by rs2k on 2012-11-10
I'm using lubuntu and the alternate CD which only needs 64 mb to install and 50 - 60 mb of RAM to run.

[http://www.wikivs.com/wiki/Lubuntu_vs_Xubuntu](http://www.wikivs.com/wiki/Lubuntu_vs_Xubuntu)


I'm afraid telling it to go with the desktop installation instead of the minimal installation is where I messed up though


At what point does the boot loader get installed? What will happen if I restart the PC right now?


UPDATE: Almost 2 hours later and the next step is happening: "Reading State Information" lol

---

### Post by rs2k on 2012-11-10
> **Bucky Ball said:**
> Yea, there's no chance of getting Ubuntu to work on a machine with 128Mb of RAM and even though Lubuntu says it will, that's very doubtful, too.  ;)

From their website:



They mention they've achieved an install with 128Mb RAM but don't explain what hoops they may have jumped through to get there. Gold star for your efforts so far and another if you can get this up, but don't like you chances ... good luck.

haha, thanks. This laptop was on it's way out to the trash anyway. I thought I'd at least try and turn it into a document reader. The install is moving again. I guess it just took a post to this site to get it moving again.

---

