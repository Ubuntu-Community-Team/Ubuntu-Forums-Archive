---
title: "Kubuntu kernel panick during instalation"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by timeh on 2007-04-26
ok so i have tried two different hardrives, i have tried kubuntu and college linux, (which i had running on this system about 2 years ago but my sister needed a temp computer so i put windows on it for her) so when i start up the installer it does two things
some times it will  say crc error system halted
and the other times it will say kernel panick VFS (and even once in a while ill get a tried to kill init error?????how is that possible)

anyways if anyone can help me
i have a sneaky suspicion that if i can partition it with the right partitions it will work but i dont have an fdisk utility or a linux boot floppy

please help im SO frustrated

---

### Post by rillip on 2007-04-26
If you're looking for a partition utility, gparted has a liveCD.

You say you're getting these errors at start up - are you booting from a liveCD or is this actually installed?  CRC error is cyclic redundancy check, indicating there's an error with one of the files being corrupt some how.  If you're booting from a liveCD, I suspect the disk is bad and you will need to reburn the ISO at a slower speed.  I'm betting if you run the check disk you'll find it's checksum is wrong.

If you've had it installed in the past and are just booting... that is very odd.  I would recommend reinstalling.  If you left your home directory as it's own partition you can do so without loosing your information.

---

### Post by timeh on 2007-04-26
is cant be a bad disk because its an official release and i did the check disk and it said it was fine, its a liveCD im booting into, its not even installed yet these errors happen when i try to install it, this is an formatted computer with nothing on it right now this is why i think it may have somehting to do with the partitioning, but i dont know because the installations usually come with partitioning sofware already dont they? im g oing to try gparted thank you but any more help will be useful

oh yeah and i tried getting help from slax but unfortuanately i think i have video card incompatabilities with it because the screen goes blank on it and/or also wont load entirly

---

