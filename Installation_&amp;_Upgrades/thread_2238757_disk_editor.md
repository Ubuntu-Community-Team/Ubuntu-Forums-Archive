---
title: "disk editor"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by Anthony_Mendoza on 2014-08-09
I want to look at the MBR of my hard drive at a binary (hex) level.   I think what I need is a disk editor.  Does anyone know of a disk editor they would recommend that I could use on a bootable USB?  Thanks. (I also don't mind paying a reasonable amount for a good tool).  The file system that I am trying to probe is of vfat type.

---

### Post by LostFarmer on 2014-08-09
I use "wxHexEditor'  or I use 'dd' to read the data into a file and then use 'bless' to look or edit it and then write it back with dd.  Its all free.  be very careful if you edit anything on the hdd with any program, it can make your system unusable.

---

### Post by Anthony_Mendoza on 2014-08-10
Thanks.  It looks like wxHexEditor will do the trick.  Thanks for the warning too.  I do have a question though about your warning.  When you say make the system unusable, do you mean permanently or do you mean until I erase the disk and reload it?  If it is permanently, how can that be?  Is there something on the disk that eraseing it won't fix?

---

### Post by LostFarmer on 2014-08-10
just may have to reload the OS and loose all data.

>  Is there something on the disk that eraseing it won't fix?] there is but it would require a very special program that we can not very likely get, would be hdd manufacture type software. Every hdd does have firmware on it but is not accesable by us.

---

