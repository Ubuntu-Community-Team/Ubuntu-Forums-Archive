---
title: "What file system to install onto?"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by Dracosama on 2005-07-04
I am using partition magic to split my sata striped raid into two parts.  My windows install (the one I am currently using) and a empty partition for ubuntu.  What should I use when I format the partition?  NTFS, Fat32, Linux Ext2, Linux Ext 3?

---

### Post by darkpark on 2005-07-04
i created the partitions with partition magic, but i left them unformated.  i formatted durning the installation of ubuntu.

to answer  your question, though, use ext3.

---

### Post by WildTangent on 2005-07-04
it doesnt matter how its formatted, installation will reformat it anyway. if youd like to know what FS to use for the linux installtion, id have to say reiserfs, but the default, ext3 is pretty good as well. just go with the default if youre new to linux

-Wild

---

### Post by Omnios on 2005-07-04
use chdisk -r to scan for bad secors etc before the partion. Should stop any bad partition tables as many people have learnt the hard way.

---

### Post by brim4brim on 2005-07-04
Don't format them using partition magic.  I did this and realised when I was installing it that 1) Ubuntu doesn't like the way Partition Magic formats Linux Partitions and 2) if you leave it as unassigned space i.e don't format it to any partition or if it's on a partition delete it and leave it as completely free space then the Ubuntu Partition manager thing will be able to everything for you assigning the swap file and everything and format to right filesystem.  It's really easy if you leave it as free space.

---

