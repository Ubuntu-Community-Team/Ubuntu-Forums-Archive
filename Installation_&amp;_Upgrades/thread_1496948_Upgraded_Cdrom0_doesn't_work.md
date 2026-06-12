---
title: "Upgraded: Cdrom0 doesn't work"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by OpenJohnson on 2010-05-29
Just upgraded from Karmic to Lucid through the upgrade manager. It had some problems and couldn't complete entirely (but almost seems as if it did). One of the problems appears to be with the Cdrom. I tried doing a fresh install with an iso burned on the disc, but it could not mount. Then I inserted a music cd, and the following message appeared:

                                 mount: block device /dev/sr0 is write-protected, mounting read-only 
 mount: wrong fs type, bad option, bad superblock on /dev/sr0, 
        missing codepage or helper program, or other error 
        In some cases useful info is found in syslog - try 
        dmesg | tail  or so
 
Is there a way to fix the cdrom or another way to fresh install?

---

### Post by bildr on 2010-05-29
mkdir /media/cdrom1
mount -F iso9660 /dev/sr0 /media/cdrom1

unless it's burned in UDF format.

---

