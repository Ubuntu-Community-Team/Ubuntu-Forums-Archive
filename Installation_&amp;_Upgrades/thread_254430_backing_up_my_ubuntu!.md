---
title: "backing up my ubuntu!"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by cope on 2006-09-09
Well its at the point where everything is where i want it! 
but i want to try get MacOSX a go on my toshiba lappy.. now i'm pretty sure its going to kill my ubuntu install, and so i want to back up my entire ubuntu partition (i have a usb drive) if i tar-gz the whole drive and copy it onto my usb drive, (300gb) can i then copy it back over and expect everything to work fine?

The only problem i can really foresee is the boot sector might be overwritten..

so my solution was to install macosx, then on the other partition install a fresh copy of ubuntu, and then copy my backup to the ubuntu partition (without copying grub's file)

---

### Post by mssever on 2006-09-10
A tarball will preserve file ownership and permissions, but you'll probably have to reinstall Grub, unless MacOS knows how to play nice.

---

### Post by aysiu on 2006-09-10
Try [using PartImage](http://www.psychocats.net/ubuntu/partimage.html) to back up your partition.

---

### Post by Original Brownster on 2006-09-10
Hi,
I would recommend you look at [Mondo]("http://www.mondorescue.org/") which will do what you want I think.
The package is in the repo's.

---

### Post by mssever on 2006-09-10
I wish I'd have known about Mondo when my hard disk died. I only know about PartImage, but since I was trying to backup to a FAT32 filesystem, I had no end of filesize-related problems. It appears from a quick glance at the Mondo page that it would have solved that problem and saved some data!

---

### Post by Original Brownster on 2006-09-10
Yes, I have had the bitter experience of H/D failure twice now, and though I did have important data on back ups I lost a bit.

I now sync my data to a second disk automatically each time the pc shuts down, in addition to hard backups!!!

---

