---
title: "New computer, old installation transfer"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by superarmy on 2008-06-23
My old computer broke down and I am about to order a new one, I would like to transfer my entire previous ubuntu installation. It was installed on and external hard drive and I would like to put it on the new computers internal hard drive. The only way I can think of is running an Ubuntu live disk and tranfering all the files from the external to the new internal. Would this work? If not, what can I do to achieve this?

---

### Post by superarmy on 2008-06-23
bump

---

### Post by logos34 on 2008-06-24
Here's the way I'd do it:

Easiest way (simple, but takes longer because it copies the entire drive, including unused space):

**dd **

E.g.:
> **sudo dd if=/dev/sdb of=/dev/sda conv=notrunc,noerror**where sdb is external usb drive, and sda is new (same size or larger) internal drive.  Make sure to get the 'if=' (source drive) and 'of=' (destination drive) correct, otherwise you will erase your ubuntu. 


OR

[Gparted (->'copy' option)]("http://gparted.sourceforge.net/larry/move/move.htm")

OR

Faster (copies only used blocks, but you'd need a space to store the image before restoring it to destination drive):

[Partimage]("http://www.partimage.org/Main_Page")

You need to work from a live cd (root cannot be mounted).
 

Then [install grub to the MBR]("http://ubuntuforums.org/showthread.php?t=224351") of the new drive.

---

