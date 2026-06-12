---
title: "cant install ubuntu with xp its says   The resize operation has been aborted"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by poopan on 2008-10-22
ive tried to install ubuntu but when i get to the part of partition
it give me this messege
 An error occurred while writing the changes to the storage devices The resize operation has been aborted 
i have 250GB hard drive
and the xp is installed on the all drive
so ive tried to resize it to 150Gb but its give me this messege can u help me? ty

---

### Post by anystupidname on 2008-10-22
My guess is that the NTFS volume's dirty bit is set and so the resize refuses to take place in case it would corrupt that volume. I suggest you try the parted magic unetbootin utility you can find here:

[http://lubi.sourceforge.net](http://lubi.sourceforge.net)

---

