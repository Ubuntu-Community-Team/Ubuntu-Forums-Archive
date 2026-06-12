---
title: "Preparing for 10.04 release...question?"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by D3mon_Spawn on 2010-04-27
I have a laptop dual booting win7 and ubuntu 9.10. I use the GRUB bootloader and have 320g HDD. 60g partition dedicated to ubuntu and 260 dedicated to Win7. When the new 10.04 release comes out I want to have it on the larger partition. I was wondering if I leave the configuration of my laptop the way it is and install 10.04 on the larger partition and reinstall Win7 on the smaller one will I encounter any major problems?

---

### Post by zvacet on 2010-04-28
If you want to delete all partitions then install Windows7 first and then Ubuntu.One more thing;if you want to give Ubuntu 260GB then it is good to make separate home partition during install.Give root /  10GB and few GB to swap and let rest be your /home partition.

---

### Post by Zafrusteria on 2010-04-28
Also make sure you put Windows on the a primary partition and best to make that the the first primary partition too. MS Windows is a little finicky about where it goes. Linux on the other hand can be installed and booted from anywhere Primary or logical. :)

---

