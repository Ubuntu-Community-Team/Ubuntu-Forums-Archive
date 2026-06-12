---
title: "How do I Dual Boot ubuntu and PcLinuxOS"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by kirtan on 2007-03-20
My 

hardisk partitions  are as following

sda1 ====> Ubuntu
sda2 ====>    Extended partition
                    [ - ] sda5 ===>swap 
                    [ - ] sda6 ===>Fat32 (For storage)
sda3=====>Fat 32             ( I want to Install** PC Linux OS** Here)
sda4=====>Fat 32             (For Storage)

Help me please

---

### Post by confused57 on 2007-03-20
> **kirtan said:**
> My 

hardisk partitions  are as following

sda1 ====> Ubuntu
sda2 ====>    Extended partition
                    [ - ] sda5 ===>swap 
                    [ - ] sda6 ===>Fat32 (For storage)
sda3=====>Fat 32             ( I want to Install** PC Linux OS** Here)
sda4=====>Fat 32             (For Storage)

Help me please

When you install PCLinux OS, select to install it's grub to the root partition(/dev/sda3)...I think you have this option near the beginning of the installation...make sure you use ext3 filesystem(not FAT32).  You should be able to use the same swap partition as Ubuntu.   Then all you would need to do is add an entry to your Ubuntu menu.lst to boot PCLinux, using chainloading:

title   PCLinuxOS
rootnoverify  (hd0,2)
chainloader +1

There's more info here:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Added:  I would go ahead and install the PCLinuxOS-TR3, it seems pretty stable to me.

---

### Post by kirtan on 2007-03-20
Thanks Friend.Thank you very much

---

