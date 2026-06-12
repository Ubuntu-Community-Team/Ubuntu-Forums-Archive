---
title: "installing on primary harddrive, second partition"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by akcom on 2006-07-13
After attempting unsuccessfully three times to install ubuntu and dual boot my computer, I've given up.  I just want to get some sort of functional operating system running (I've been running off a live cd for 3 days now).  Windows is the primary partition on my primary HD.  I want to preserve that data and get ubuntu installed and working on the rest of the HD space (about 90 gigs).  Going through the normal livecd install process does not work.  When I restart the computer, regardless of the many changes I've made to the configuration, GRUB dies at step 1.5 (error #17, although I have a feeling it has nothing to do with the filesystem used).

---

### Post by Jagot on 2006-07-13
Have you tried using the Alternate Install CD?

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

To be honest I prefer that to the Live CD installer.

---

### Post by akcom on 2006-07-14
I just attempted an install with the Alt. CD and things went poorly.  My computer refused to even boot from the CD.  Any other suggestions?

edit:
After a helpful suggestion from #ubuntu, I burned the Alternate CD at 4x, which (surprise!) made it work.  So now I tried the install using the ALT CD and grub still dies at step 1.5 (error #17).  I've tried the following configs:

hd0,0   Windows XP (NTFS)
hd0,1   /boot (ext2, bootable)
hd0,2   / (ext3)
hd0,3   swap (linux-swap)
hd1,0   /shared (fat32)

and:
hd0,0   Windows XP (NTFS)
hd0,1   / (ext3)
hd0,2   swap (linux-swap)
hd1,0   /shared (fat32)

I have also tried installing grub to the bootable partition with no success.  Any suggestions?

---

