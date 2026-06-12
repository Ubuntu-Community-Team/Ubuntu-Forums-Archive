---
title: "No Linux work on my computer"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by Cnaeus on 2011-05-16
Seriously, I have no idea what's going on. My desktop computer runs fine  with winXP, but recently I decided to move to linux, because I use  linux on my laptop and it's quite a pain setting up a LAN connection  between a linux and a windows machine. Anyway, the fact is, linux  distros won't even boot on the desktop pc. I tried Kubuntu/Ubuntu/Bodhi  linux live CD-s, tried Arch Linux and even Pardus 2011. The live cds  just freeze at the bootup logo screen, and simply wont go anywhere.  (after I choose the start kubuntu option) The others cant make it to the  installation either. I Also tried to boot from USB: I created a  bootable USB with "unetbootin-win-549". It simply said nothing more than  "Boot error.
Now every live cds and bootable USBs runs fine on my laptop, so I guess the problem is not there.

Problematic Desktop PC specs:
Asrock 94i65GV Motherboard
1024 Mb RAM
Intel Celeron 2.40Ghz processor
Nvidia Geforce MX440 graphics card

thanks for help

---

### Post by sanderd17 on 2011-05-16
Check my signature to set boot options, and try setting the "acpi_osi=" and the "xforcevesa" option (without quotes, with the =-sign). If you need to use vesa, you won't have accelerated 2D and you won't have 3D. But maybe we can see the problem that way.

---

### Post by Cnaeus on 2011-07-31
Ah, I found out that AsRock motherboard are not stable under linux kernel while using the AGP slot... So I have to use the integrated graphics if I want to use AsRock motherboard with linux, and have to unplug the nvidia card...

---

