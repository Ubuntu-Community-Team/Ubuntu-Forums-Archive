---
title: "GRUB/LILO/BOOT MAGIC...Wich one?"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by Bari40 on 2005-07-20
I would like to install Ubuntu Hoary 5.04 and have a dual boot with WindowsXP.If I install Boot Magic, do I have to install GRUB or LILO? If yes, where is best to install them, in the MBR or in Linux partition? Also if I partition the hard-drive with Partition Magic, how many partion do I need to install Ubuntu. I have 60Gb free on a slave drive. Many thanks to anyone who can help
Mike

---

### Post by adwait on 2005-07-20
LILO, I beleive is older. GRUB is the one mostly used. Boot Magic is non free, but if you have bought it/want to buy it.......why not! It miight be a lesser pain than to setup with GRUB with XP.

Let partition magic create unformatted space and then make the partitions through the ubuntu installer. 
/
swap

These are the only two partitions you need. swap should be about twice as much as your RAM. and / can be any size you want..10 GB should be fine.

Load the bootloader to the MBR.

---

### Post by codejunkie on 2005-07-20
[QUOTE=Bari40]I would like to install Ubuntu Hoary 5.04 and have a dual boot with WindowsXP.If I install Boot Magic, do I have to install GRUB or LILO? If yes, where is best to install them, in the MBR or in Linux partition? Also if I partition the hard-drive with Partition Magic, how many partion do I need to install Ubuntu. I have 60Gb free on a slave drive. Many thanks to anyone who can help
Mike[/QUOTE]
It would be best to use grub and install it to the MBR of your first hard drive hda, as for how much hard disk space you need i think they recommend 4-5 gig that is assuming you want to install a decent amount of software.

---

### Post by Bari40 on 2005-07-20
Thanks a lot to adwait and codejunkie for their response. I'll follow your advice.

---

