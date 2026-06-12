---
title: "CDRom Partion information wrong ???"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Nortonw on 2007-07-13
:confused:I'm having huge problems trying to install Ubuntu on a Fujitsu Siemens f200 server.

Using the internal CD drive the check disk fails constantly and the install dies at about 2%.

If I plug in an external USB cdrom drive and boot from that the install completes ok.
Once I am at the command line I use Fdisk -l /dev/cd* 
This is showing 2 devices which are both the same drive /dev/cdrom and /dev/cdrw

It also shows errors relating to partition information being missing and complains that the sector size is 2048 and not 512 ?????????????

This is the internal drive it is reporting on not the external usb drive.
I have no idea what the external drive is called or how to mount it etc.
I need to be able to run apt-cdrom add but it cant read the CDs ????

How can I change this 2048 to 512 ??
If I do will it work??
I have tried 3 differnt types of internal drive for this machine and they all do the same.

Please help as I have spent weeks getting this build perfect on an HP DL380 and didnt think I'd have any issues on the Fujitsu box.

---

### Post by Nortonw on 2007-07-13
Looking at other articles it would seem that alot of people have had similar issues.
I cant however find a fix ???????

My CDrom is seen as a SCSI device even though its an IDE drive??
Can someone please help me

---

