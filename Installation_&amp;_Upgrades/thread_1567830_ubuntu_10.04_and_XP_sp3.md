---
title: "ubuntu 10.04 and XP sp3"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by tony van on 2010-09-04
computer 8300 dell 82875 intel 
 
setup as follows:
drive A master xp installed
dev/sda master boot 
 
filesystem dev/sda1
 
drive B slave ubuntu
dev/sdb (grub 2.863gb)
 
grub.cfg set root=(hd1,1)
until it gets to microsoft home edition, it changes to
(hd0,1)
drivemap (hd0)
 
it automatically boots in XP
 
i followed an example on windows xp in the forum for dual boot.
 
 
fdisk -L
 
 
drive 2 boot
DEV/sdb1 * linux 
dev/sdb2 extended
dev/sdb5 linux swap
 
drive 1
dev/sdc1 ntfs
is it the bios or grub ?
help appreciated:D

---

### Post by davidmohammed on 2010-09-04
whats the problem?  I don't understand what you are trying to say.  What are you seeing on the screen?  Any error messages?

---

### Post by tony van on 2010-09-04
I found my problem . I did not format the drive. i formatted it re-installed and it booted into ubuntu. for me this ia an accomplishment.

---

