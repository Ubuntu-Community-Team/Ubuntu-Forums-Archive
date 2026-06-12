---
title: "Install onto sata drive"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by seanhobbs on 2008-02-13
I have a segate sata drive installed on an intel ich7 chipset.  when i try to install ubuntu i get a filsystem not recognized error, but it manages to erase the previous install of windows that was on the drive.  do i need to install a driver at startup like the "f4" in windows install?  If so, how do i do that, i am never asked if i need to install any additional drives.  I did get it to install on another machine that has the ich9 chipset but used an old ide hard drive.  Is ubuntu able to install on sata drives?

thanks

Sean

---

### Post by Pumalite on 2008-02-13
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst
(Boot your Live CD if you don't have a working system)

---

### Post by NIT006.5 on 2008-02-13
Not my area of expertise, but I know I've installed onto sata drives with no problems at all before, and my PC is running ubuntu on sata as well. So must be something specific to do with that hardware I would think.

---

### Post by froy02 on 2008-02-13
Most probably a bios setup on the intel motherboard. Check your bios to see if you have a line "SATA AHCI".  If you do, enable it.

What this does is overcome the hard-drives limitations even if drivers are not loaded yet.  On most other motherboards' chipsets this not a choice but it is on intel chipsets.

If that does not fix it try changing "SATA Port0-1 Native mode" also. 

I am almost sure that those 2 above are the what I changed on my friend's computer when we installed Ubuntu on his computer though he has ich9 chipset.

I hope this helps.

---

