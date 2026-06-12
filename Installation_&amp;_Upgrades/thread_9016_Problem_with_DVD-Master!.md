---
title: "Problem with DVD-Master!"
date: 2004-12-23
forum: Installation &amp; Upgrades
---

### Post by paradox on 2004-12-23
Hi!

I have a LG DVD multi recorder. 

dmesg | grep HL 

hdd: HL-DT-ST DVDRAM GSA-4082B, ATAPI CD/DVD-ROM drive

In other Ubuntu create fstab with this line:

/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto              0 0


/dev/hdd don't exist!!!!!!!!!!!! Of course Ubuntu don't mount anything! Why? I can't use this device!!!! The message is:

mount: special device /dev/hdd does not exist

You can help me? TNX!!!

---

