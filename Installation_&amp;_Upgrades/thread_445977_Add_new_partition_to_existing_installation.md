---
title: "Add new partition to existing installation"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by nubie777 on 2007-05-16
I want to add new partitions to an existing ubuntu-edgy installation that is beginning to running out of space.  Please see the attached jpg image of my disk drive layout created by GParted.

Here is what's on the drive:
hda1 - win xp
hda3 - existing, fuctional ubuntu installation
hda5 - ubuntu swap 
hda 6,7 & 8 - ext3 partitions that I want to add to my existing ubuntu installation. Hda 6,7,8 use to be a suse installation.

The location of the ubuntu swap file (hda5) is in an unusual place.  This box had win-xp, ubuntu, suse 10.1 and Fedora Core 6 installed before I started this task.  I trashed suse 10.1 to make room for the  ubuntu file expansion. I did not bother showing the other drives since they contain the Fedora install and an NTFS partition I use for backups.

The problem I am having is I can't create a directory on the new partitions to be used a mount points.  I can't add the mount points via mkdir because I can't see the partitions in x-windows or from the command prompt.  The mount points on the drive layout  image come from the fstab file.  The fstab file is attached.  Sorry, it's really ugly. I added the last four lines to account for hda 6,7 &  8.

 

[COLOR="RoyalBlue"]Can anyone please instruct me on how I can add mount points so the partitions become visible and available when ubuntu is running?[/COLOR]

Thanks a bunch in advance!

Note: I had to add the extension .txt to fstab to get it to upload.

Here is a link to the image: [http://rapidshare.com/files/31663359/partitions1.jpg.html](http://rapidshare.com/files/31663359/partitions1.jpg.html)
[IMG]http://http://rapidshare.com/files/31663359/partitions1.jpg.html[/IMG]

---

### Post by nubie777 on 2007-05-16
The disk image does not appear.  I'll try to upload it again.

---

### Post by nubie777 on 2007-05-16
My image dimensions are too big.  Let me work on this and report the image.
Sorry.

---

### Post by nubie777 on 2007-05-16
Hopefully the image will show up this time...

Image did not show up again.  I've posted it on rapidshare.com.  You should be able to download it w/o an account.  Sorry about all mess with the image!

---

