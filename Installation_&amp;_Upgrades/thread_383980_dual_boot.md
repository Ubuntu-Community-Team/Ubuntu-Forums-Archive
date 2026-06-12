---
title: "dual boot"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by mr.farenheit on 2007-03-13
my new notebook came with windows 05 media installed on a fat32 partition and inside my computer it shows that the hdd has been equally split with one side bein fat32 and the other being ntfs. i'm wondering if it is possible to go thorugh with the ubuntu cd and format the ntfs partition to ext format and run a dual boot os. the only problem i am seeing is when it comes to installing the boot loader, i've been told its best the have the boot loader at the beginning of the hard drive for best effectivity. is there any way i can set it up to run the boot loader farther on the drive and still manage a sucessful dual boot set up?

---

### Post by wonk-o-matic on 2007-03-13
You will like the answer: you can just do a normal install.  Installing will let you reformat the ntfs partition.  

But first, you should probably double-check the ntfs partition to make sure that it has no important files.  You can probably copy any files to the fat32 partition, if you find anything there.  

Don't worry about the boot loader.  GRUB will work fine, no matter which partition you install Linux on.  I have done this on a couple of machines, some old, and some new, and never had a problem.

---

### Post by mr.farenheit on 2007-03-14
so even if the boot loader isn't at the beginning of the disk it will still work?

---

### Post by zvacet on 2007-03-15
Just listen wonk-o-matic advice.

---

