---
title: "Difficult Install issues"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by Agrajag27 on 2008-03-31
Guys, I own an Intel D975XBX2 motherboard with Quad Core Extreme processor.
EVGA 8800GTS 640
Sound Blaster X-Fi
Windows XP Pro SP2

My hard drives are as follows:

HD0 is an IDE drive with my "F" partition (NTFS) on it first storing all my music. Linux EXT3 is second (25GB) and finally a 1GB Linux Swap drive.

HD1 has my NTFS Windows setup on it (drives C, D, E) and is a SATA drive.

I tried to install Ubuntu using the LiveCD but it fails to boot properly reporting a generic "Failed to Allocate Mem Resource" error.

I then tried the Alternate CD install and that seemed to work. The final step was for Grub to get setup and it seemed to install and then I was told to reboot and enjoy the new OS.

When I reboot, however, XP comes up instantly with no GRUB.

I have an Ubuntu friend who's pretty knowledgeable and we tried for 3 hours to get it to work. We can get GRUB to come up by forcing it to install on HD1 (it installs on HD0,1) but then when it shows up it claims it can't mount the Unbuntu drive and reports that NTLDR is missing for XP. After a repair XP is fixed but then GRUB is gone.

Anyone know what's up so I can finally join the Ubuntu wave????

(Swapping the Hard Drive Device order fixed this for me.)

---

### Post by manishsk on 2008-04-01
hi 

Try [this]("http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot").

I believe this should solve your problem. Do not connect your windows drive when you are installing Linux. Connect it after the install. You can Enjoy windows after few modicifcations in the menu.lst file. I have tried this and it wroks really well.

I have 1 HD with windows. Another with windows and Ubuntu. I can switch any of the 3.

Check if you Ubuntu disk is master or not.

---

