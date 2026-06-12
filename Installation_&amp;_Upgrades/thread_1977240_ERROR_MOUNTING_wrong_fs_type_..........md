---
title: "ERROR MOUNTING: wrong fs type ........."
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by alpinehammer on 2012-05-09
Hi
I have a dual boot (ubuntu 11.10 and Win XP). After re-sizing some of the partions I was unable to re-boot the computer. Using a Live CD and the boot repair app I am now only able to boot into Win XP.

Using the Live CD, when I try to mount '33GB File System' I get the following message - ERROR MOUNTING: mount: wrong fs type, bad option, bad superblock on /dev/sda5 etc......

After lots of searching on here I ran 

$sudo e2fsck -C0 -p -f -v /dev/sda5

which returned the message:

/dev/sda5 UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY

I then ran 

$ sudo e2fsck -y -f -v /dev/sda5

this eventually returned a message (see attachment) ending 

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
e2fsck: aborted

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****

Any help would be greatly appreciated

---

