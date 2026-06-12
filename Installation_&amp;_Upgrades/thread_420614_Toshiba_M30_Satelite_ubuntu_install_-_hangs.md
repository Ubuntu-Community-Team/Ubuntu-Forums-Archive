---
title: "Toshiba M30 Satelite ubuntu install - hangs"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by SL666 on 2007-04-23
Hi Guys, 

Boots from CD (7.04), installs without error, can see every thing, everything pretty much works.

after the reboot (removing the CD) straight after POST it just goes to the message

GRUB _


and thats it, can't type, can't do anything - the underscore flashes quickly.

If we put in the live CD again, we can boot from the hardrive, and its fine.

- can't find any extra partitions.

tried [http://ubuntuforums.org/showpost.php?p=121355&postcount=5](http://ubuntuforums.org/showpost.php?p=121355&postcount=5) - grub config stuff, still no go.

everything functions perfectly once booted off the CD.

Any ideas where to try next?

Cheers Steve.

---

### Post by SL666 on 2007-04-23
We have now tried the supergrub - fix grub commands, still no go.

---

### Post by SL666 on 2007-04-24
fixed now.. zero-fill on the drive, then installed fine.

---

