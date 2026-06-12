---
title: "Using Grub to install Hoary from my C:\ drive"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by dubside on 2005-04-12
I’m trying to install Hoary 5.04 on my XP machine (alongside XP, not over it), and since the installer doesn’t seem to like my cd-rom drives, I’m trying to figure out how to boot from the .iso on my XP partition.

Someone in another thread offered this guide, 

[www.knoppix.net/wiki/Win_Partition](www.knoppix.net/wiki/Win_Partition)

which looks like what I need, except that grub’s menu.lst file is set up to boot a knoppix iso. 

I’m totally new at this, so I was wondering if someone could explain how I could edit the .lst to boot from, say, C:\BOOT\Ubuntu 5.04.iso. I don’t actually want a Poor Man's Install—I just want to get Ubuntu installed on its own partition so I can then set up the proper drivers for my cd-rom drives...

I've pasted the text of the existing .lst file below, deleting additional titles that I'm pretty sure aren't needed (like options to boot from older kernels of knoppix).

Thanks




################################################## ####
# GvR Dec 16th 2004
color black/cyan yellow/cyan
timeout=5
default=0

title Default Boot on HD 0
rootnoverify (hd0,0)
chainloader +1
boot

# Knoppix Boot from a single NTFS partition hda1:
# All the files within the directory "Root_Of_NTFS" of the grubd.zip
# have to be copied into the root of the NTFS hda1 partition c:\
# but the boot.ini file (which is just here as an example,
# the line "c:\grldr="Start Grub" has been added at the end of the boot.ini)
# Copy the also the 700MB knoppix ISO file into c:\boot\knoppix.37\ directory

title Knoppix 3.7 kernel 2.6 from NTFS hda1 ISO scan ramdisk=32MB
kernel (hd0,0)/boot/knoppix.37/linux26 ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 nomce quiet bootfrom=/dev/hda1/boot/knoppix.37/*.iso config=scan home=scan ramdisk=32768 noprompt
initrd (hd0,0)/boot/knoppix.37/minirt26_ntfs.gz
boot

---

### Post by dubside on 2005-04-13
Anyone?

Actually, any alternative installation suggestions would be welcome--I just want to get Hoary on the machine  :)

 I also tried using my iPod as a USB boot device, but that didn't work. I'm not sure whether that's because I did it wrong or because you just can't use an iPod like a flash USB drive??

---

### Post by vnbuddy2002 on 2005-04-13
For IPOD, I am pretty sure that you can not use IPOD as the booting device. Unlike other USB drives, IPOD hard drive requires a special driver to mount.

---

