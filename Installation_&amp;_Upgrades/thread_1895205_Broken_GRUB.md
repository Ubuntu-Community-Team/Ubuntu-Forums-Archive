---
title: "Broken GRUB"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by THE_An0mOLy! on 2011-12-14
Okay so this has come about from me trying to install kubuntu over (i.e. by formatting) my openSUSE and Chakra partitions.

In any case I'm guessing I screwed up setting the mount points whilst manually setting the partitions during the install.

I've been trying to use super grub disc 2, ultimate boot disc and the kubuntu disc itself to fix the problem and have successfully made it worse ^^


Whenever I boot normally to my hdd it comes up with:
"error: no such device:... grub rescue>"

and when I list devices I get hd0 but then others such as:
hd0,msdos1  
hdo,msdos 2  
hd0,msdos5
boot
boot/(something else)

When using super grub disc it says it can't find any grub installations... but it found 2x grub config files, using one i managed to boot into kubuntu and tried to reinstall grub but to no avail - it still says there are no grub installs and fails to boot.

I've also managed to break my MBR since gparted says the entire hdd is unallocated...

I don't mind removing linux completely (leaving win7) and then reinstalling but I'm just not sure which step to take first ^^


Any help is greatly appreciated :D

---

### Post by THE_An0mOLy! on 2011-12-14
Mark as SOLVED please :)


Used Super Grub Disk to boot into win 7 and format all other partitions, then used win 7 recovery disk to do startup repair + reinstall the win7 MBR then simply reinstalled kubuntu :)

---

