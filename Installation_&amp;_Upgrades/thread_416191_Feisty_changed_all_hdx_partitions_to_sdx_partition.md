---
title: "Feisty changed all hdx partitions to sdx partitions"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Patrick K on 2007-04-20
All my partition have had their names changed by Feisty from hdx type names to sdx names.  

In both fstab and mtab the sdx names are used. Yet, if I boot to Edgy both files use hdx names. Both hard drives are IDE. Only two FAT32 partitions of 11 (don't ask :)) mount properly, both are IDed by UUID number. The rest don't have UUID numbers.

I looked in Device Manager for UUID numbers for the unmounted partitions but only the two that are mounted have them. 

Also, I looked in /dev/.udev/db and all the partitions listed there have sdxx as the last letters of the filenames. Opening the files, only the two FAT32 partitions that mount correctly have UUID numbers, the unmounted partitions don't. 

Fortunately, /,  /home and the two FAT32 partitions mount correctly, but swap doesn't.  

What is the best way to fix this? Changing all references from sdx to hdx seems like a iffy job since all the files in /dev/.udev/db probably need to be changed. I doubt making up UUID numbers would work (how are these generated?).

Is there a way to regenerate fstab and mtab? If so, would this correct the files in /dev/.udev/db?

---

