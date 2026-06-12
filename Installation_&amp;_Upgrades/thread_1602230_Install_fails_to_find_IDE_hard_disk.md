---
title: "Install fails to find IDE hard disk"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by ufbh on 2010-10-21
Hi.

Trying to install Ubuntu 10.04 64 Bit Server fails on a Tyan S2882 board. The installer does not find the hard disk connected to the frist IDE/ ATA controller. The install cd boots from the IDE DVDROM connected to the second IDE/ ATA controller without problems.

Previously Ubuntu 6.06 has been installed on the system without problems.

It tried to fix it using nodmraid without success.

Does someone know the trick? :confused:

Best regards.
Benjamin

---

### Post by arpanaut on 2010-10-21
Has the drive ever been a part of a raid array?
If so there may be metadata remaining on the drive.

look->  [http://wwww.ubuntuforums.org/showpost.php?p=9991873&postcount=1](http://wwww.ubuntuforums.org/showpost.php?p=9991873&postcount=1)

---

