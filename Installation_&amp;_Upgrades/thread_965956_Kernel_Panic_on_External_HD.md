---
title: "Kernel Panic on External HD"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by nikRbokR on 2008-10-31
Alright... I made a successful install on the external hard drive and it seemed to be going alright.  I made the changes to the appropriate files in /etc/initramfs-tools ...

However, when I did```
nano /boot/grub/menu.lst
``` I ran into (what I think is) my problem.  See, I have 2 other hard drives on the desktop: one has XP, the other Vista.  However, XP was (hd0,0) and Vista (hd1,0) @ the VERY bottom of the file.  So I changed XP to : (hd1,0).  Higher up, I made Windows 95/98/2008 (hd1,0) and Linux (0,0).

The kernel panic I got was something like: could not find (0,0)... so I think the two (1,0)s for XP and Vista threw it off.  Could someone please help me out?  I had been able to get the external boot to work previously, but that was when only one other hard drive was present.

By the way, this is the place where I got the instructions for installing on an external drive: [http://ubuntuforums.org/showthread.php?t=678146](http://ubuntuforums.org/showthread.php?t=678146) - it just doesn't say what to do if there are multiple drives in the system (w/ more than one OS)....

Error Message:
```
[  776678] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
```

The part of my /boot/grub/menu.lst that is confusing me is this part:
```
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Not really sure how to handle that "root" (2 (hd1,0)s?) and the "map" underneath Vista

Thanks!

---

