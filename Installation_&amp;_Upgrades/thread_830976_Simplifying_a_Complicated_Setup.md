---
title: "Simplifying a Complicated Setup"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by capatt on 2008-06-16
Hello
     Over time, my system has morphed into a rather complicated arrangement, which I'd like to simplify.  Any help would be much appreciated!  Here's what I have:

C:\XP, PCLinuxOS (sda5, swap, sda7)
D:\Vista, Ubuntu 8.04 (sdb2, swap, sdb4)

Installation order:  XP, Vista, PCLinuxOS, Ubuntu.

Before I installed Ubuntu, my boot menu was configured with EasyBCD like this:
XP
Vista
PCLinuxOS.

When I installed Ubuntu EasyBCD wouldn't recognize Ubuntu's Grub installed to its own boot partition on the D:\ drive so I had to install it to PCLinuxOS' boot sector (sda5), where it overwrote the old Grub menu with it's own.  It now presents both Linux distros and I can choose between the two. 

Boot menu now goes like this:

XP
Vista
Linux > then choose Ubuntu or PCLinuxOS

My issue now is that I'd like to get rid of PCLinuxOS and keep Ubuntu, preferably moving Ubuntu's partitions to the C:\ drive.  This would obviously blow away the current bootloader in sda5 and render Ubuntu unbootable and who knows what other complications would arise.

I hope this is all clear......  Any ideas on how to simplify this whole arrangement (yes I want to keep XP/Vista!)?

---

### Post by hal8000 on 2008-06-16
All you need to do is EasyBCD control the loading of XP/Vista and just chainload the windows XP section with chainloader +1 in the menu.lst

Boot Ubuntu, then post:

sudo fdisk -l

cat /boot/grub/menu.lst

---

### Post by meierfra. on 2008-06-16
> When I installed Ubuntu EasyBCD wouldn't recognize Ubuntu's Grub


Did EasyBCD recognize  Ubuntu not at all?
Or were you able to add  Ubuntu to the  Vista boot menu, but booting Ubuntu failed?

Did you try the "Neogrub" option in EasyBCD?

---

