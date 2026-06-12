---
title: "More Hard disk upgrade problems"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Wake Rider on 2008-02-29
I had successfully upgraded my harddisk except for I left the old one in. I noticed that files were going missing from my Ubuntu install and discovered that Ubuntu was reading both partitions as one, showing hda of the old 80GB ide disk, but 156 GB of its partition on sda (sata). When I became aware of this problem, I deleted and reformatted the old IDE disk to ntfs to use as spare storage for both Ubuntu and Windows. This would force both operating systems to only use the new 500GB sata disk. Ubuntu started up fine, reading its new partition but now I have broken Windows!:( It gets to the blue welcome screen before freezing. I have the original windows install disk, a super grub disk and a parted magic disk. Can I please have some advice on how to fix Windows while keeping Ubuntu intact?:confused:

---

### Post by logos34 on 2008-02-29
Boot into the windows install cd REcovery console and run error check w/ repair option:

**chkdsk /r**

and 

**fixboot**

Windows is picky and notices any changes to its 'environment' (like when you copy it to a different disk).  You may have to reinstall.  Can you mount windows in linux?  If so, then you could backup all your personal files to the other disk.

---

### Post by jeffus_il on 2008-02-29
> "Alcohol and calculus don't mix.  Don't drink and derive." 			
So drink and integration is recommended?:)

---

