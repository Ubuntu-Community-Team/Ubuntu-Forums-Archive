---
title: "From Grub Error 18 to Grub Error 15"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by The King Kuranes on 2005-08-09
Thanks in advance for any help I can get. I've tried Linux before with various degrees of success but never accomplishing a perfect fully functional instalation. Now I'm trying to install Ubuntu in my box without wasting my existing XP system (my family
will kill me if I do). I'm trying to install Ubuntu in a Lacie USB external drive with 40 Gb.
My goal is to be able to boot from there, isolating the linux installation from windows (My BIOS can handle usb boots, if anyone asks).

 First I follow all the usual installation without problems, installing GRUB in MBR of the USB drive (/dev/sda). When i boot, appears "Error 18" in the stage 1.5 and hangs without mercy.

 Investigating a while, I found that "Error 18" points to the 1024 cylinder limit or in modern BIOS like mine the 8Gb limit. The first partition was 38.5 Gb (sda1) with a swap of 1.5 Gb so the error makes sense if boot is located in /dev/sda1. For solving this I reinstalled Ubuntu with the following partition structure:

  -/dev/sda1 a /boot primary partition with 256 Mb and ext3
  -/dev/sda3 a / primary partition with 38.2 Bf and ext3 for the system itself
  -/dev/sda5 as the usual 1.5 Gb swap partition

When booting with this configuration I found that "Error 18" has morphed into 
"Error 15" which means apparently that Grub cannout found my kernel. Using a
Knoppix Live-CD distro as rescue disk i was able to access the drive and examine
the /boot partition. Apparently the vmlinuz and initrd files where there so I check
the menu.lst file and discover nothing (I'm not a GRUB expert). Anyone knows how I can fix this? Not being able even to boot the system is kinda frustrating. If anyone needs to see the menu.lst file I can post it on demand. Again thanks.

---

### Post by blind0wl on 2005-08-10
When you used your knoppix boot disk, did you actually mount the /boot partition?  By default you have to mount the main / partition and then mount the /boot within it.

---

