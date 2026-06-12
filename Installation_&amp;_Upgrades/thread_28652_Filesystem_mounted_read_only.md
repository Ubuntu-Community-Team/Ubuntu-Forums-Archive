---
title: "Filesystem mounted read only???"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by Grasshopper_NZ on 2005-04-21
Hi everyone, just made the switch from windows xp to ubuntu. 

On bootup a line appears saying the filesystem is mounted read only. I've only installed ubuntu and the only change i've made is mounted my windows partion as stated on the userguide.  

I cant right click in natulis and create folders, is this normal?? or im i still living in the world of windows. 

my fstab settings

<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1	/mnt/windows	ntfs	umask=0222	0	0

is this correct anyone??

Also can anyone point me in the right direction for sites that will teach me how to mount my other hard drives and basic linux stuff.

Thanks heaps

---

### Post by CrustyDOD on 2005-04-21
Yes its normal as almost everything outside your own home folder is protect so that only root user can change files..

Something like if you're a limited user in windows.

So to create new folder use sudo command in console, that's how i do it: sudo mkdir /foldername

ups and if you're are talking about windows partition, as far as i know, if its NTFS its read-only, that's why i have FAT32 still on windows  :) 
Experts will tell you more :)

---

### Post by Grasshopper_NZ on 2005-04-21
Thanks, thought something went wrong during the install.

Does make sense now. 

Must say Ubuntu does rock from the little i've seen. I look forward to enjoying th e great world of linux.

---

