---
title: "add dvd drive"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Jeffreyharter on 2007-10-30
I have replaced a cd-writer with a dvd-writer; when I try to play movies in Kaffeine, the system reports that xine-engine could not start.  Ubuntu still thinks I have a cd-writer installed rather than the dvd-writer.

How do I tell the system that the "cdrom" is gone and a dvd is presetn?

Thanks...Jeff Harter

---

### Post by logos34 on 2007-10-30
you need to create symbolic link(s) 'dvd' and 'dvd-rw' in /dev directory pointing to /dev/hdc or /dev/scd0 or howver it's listed in your /etc/fstab.

---

### Post by alnhntr29 on 2007-11-04
and for someone who doesnt know how to create a symbolic link?
I am not ubuntu illiterate, just have the same problem. Added a dvdrom/cdrw and it gets recognized off the bat with the 6.06 live cd but I cant figure out how to make gutsy see the drive. Used the live cd to format a hdd(another problem I have) Gparted hangs with gutsy, worked fine off the cd, and had a dvd in the drive when i booted and it came up fine.

---

