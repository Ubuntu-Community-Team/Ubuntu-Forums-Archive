---
title: "Grub"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2008-02-15
I have more than one harddrive and I installed Ubuntu 7.10 on my sata disk.

This is the layout:
Primary IDE Master 
Primary SATA Master

Ubuntu is installed on the SATA disk but the first disk is the IDE disk, so does that mean the IDE disk should be marked as *boot* and grub should be installed on that IDE disk?

---

### Post by logos34 on 2008-02-15
Grub should be on the MBR of one of the two disks.  (it usually installs on the IDE in cases like this).  Switch the hard disk boot order in the Bios.

---

### Post by tbresson on 2008-02-15
I can't change the order in which the bios chooses IDE before SATA and the SATA disk is the first in the boot order in my bios.

---

### Post by logos34 on 2008-02-15
[Reinstall grub from the live cd]("http://ubuntuforums.org/showthread.php?t=224351") to the mbr of the sata.

---

### Post by tbresson on 2008-02-20
Now that I understand what you meant by your previous post .. I found out that was the solution :)

Tnx!

---

