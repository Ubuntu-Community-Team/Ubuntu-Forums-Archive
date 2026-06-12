---
title: "How do I fix boot sector after partition copy"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by billstei on 2009-12-07
I replaced a hard drive with a bigger one, and used GPartEd to copy an NTFS partition from the old drive to the new one.  The new NTFS partition is larger and in a new location, and using the boot_info_script040.sh I get:

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 460920915. But according to the info from 
                       fdisk, sda4 starts at sector 1193725890. According to 
                       the info in the boot sector, sda4 has 164216429 
                       sectors, but according to the info from fdisk, it has 
                       271418175 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


What is the easiest way to fix this without disturbing grub2 and my Ubuntu install (both of which are working fine) ?

---

### Post by billstei on 2009-12-08
Nevermind, it got totally borked, so I reinstalled Windows into the partition.

---

