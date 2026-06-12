---
title: "Hard Disk not booting"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by viarand on 2008-06-04
I have bought a new 250GB sata HD.I partitioned it with gparted with /boot as primary and remaining in extended type.I installed feisty fawn.The problem is the hard disk is not booting directly.
I hav to put the CD and select "Boot from first hard disk" option to boot.I want to know whether i hav made a mistake or the problem is with the hard disk. 
       Thaks in advance.

---

### Post by viarand on 2008-06-05
Anybody help me please.

---

### Post by Dave2k6 on 2008-06-05
Did you install GRUB to the MBR or to the /boot partition ?

---

### Post by viarand on 2008-06-05
I am a newbie.I just created partitions and installed feisty.I dont know where is the GRUB installed.

---

### Post by viarand on 2008-06-05
Thanks for ur reply Dave2k6. I solved it by giving the boot flag to my extended partition using GParted.

---

