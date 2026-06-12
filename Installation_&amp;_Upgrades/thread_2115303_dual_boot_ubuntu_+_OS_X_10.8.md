---
title: "dual boot ubuntu + OS X 10.8"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by rumpumpel1 on 2013-02-12
I have a primary Ubuntu disk, which has an MBR, 
where the grub2 bootloader resides.  
On another disk I have a OS X 10.8 installation. 
The only way to boot into OS X is to choose the 
bootdisk with F12 from the BIOS menu. 
I would like to start OS X from the grub bootmenu.
There are already two generated entries for 32bit
and 64 bit, but neither of them works. Choosing
one of these entries ends with a black screen. 
The OS X disk shows the following partitions: 

Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot
 2      210MB   400GB  400GB  hfs+         Mountain Lion

So what exactly do I have to put into /etc/grub.d/40_custom in 
order to get a working entry in my grubmenu for OS X ?

---

### Post by zvacet on 2013-02-14
What type of Mac do you have?

---

