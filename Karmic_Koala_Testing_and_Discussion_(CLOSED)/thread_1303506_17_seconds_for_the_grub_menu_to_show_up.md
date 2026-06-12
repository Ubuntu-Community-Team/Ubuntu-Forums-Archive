---
title: "17 seconds for the grub menu to show up"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Najmudin on 2009-10-28
Hi
I don't know if this is normal or not, but when i start the computer it says " grub loading" for about 17seconds, then the grub menu shows up.
Is there a way to solve this issue or i should wait for some updates to solve it later on ?
Best regards

---

### Post by autocrosser on 2009-10-28
This is a bug that I've reported a couple of months ago: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

The workaround is to reorder your drives so that Grub2 & the MBR are on the First drive.

---

### Post by emarkay on 2009-10-28
[http://ubuntuforums.org/showthread.php?t=1290221](http://ubuntuforums.org/showthread.php?t=1290221)
Was also noted  a while ago.  

IMHO the drive reordering is not a solution nor a workaround; it's a "Band-aid" to cover some poor code.  Only those with the time to play around, with familiarity in Gparted" or those with data to [possibly] lose will agree this is a solution!

---

