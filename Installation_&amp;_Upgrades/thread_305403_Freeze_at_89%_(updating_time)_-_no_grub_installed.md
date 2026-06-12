---
title: "Freeze at 89% (updating time) - no grub installed"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by steffen on 2006-11-23
I have installed Ubuntu on 10-15 laptops. However, today I encountered an issue with Edgy on an IBM TP T43. This is the first time I have installed to a SATA drive, but I'm not sure if that's the problem.

Installation freezes at 89% (it says "Updating time" or something similar...) - at this time it seems all files are copied to the system, except Grub.

After a few attempts (all failing at this stage - and YES I have checked the md5 sums, check media, etc.) I decided to try and start the laptop with what's on the box. So I used the Live CD Grub installer to get Grub, but Grub didn't set up a /boot/grub/menu.lst file. When trying to boot the kernel I get error 15 and file not found (using root=/dev/sda3). I have also tried /dev/sda2, etc. and all the different (hd0,1), (hd0,2), etc. (since my drive is mapped to hd03 according to /boot/grub/device.map)

This is my company's computer, so I haven't wiped Windows. I'm able to start windows using (hd0,0) as the drive.

What's also odd is that I don't have a /boot/initrd.img-2.6.17-10-generic, but /initrd.img in the root directory instead. I've tried booting using all options, however.

It's a SATA drive, and Explore2fs in Windows can't find any /dev/sda's, but I was able to chroot and mount /dev/sda3 when in the Live CD.

Any pointers on this? I've looked through /var/log/* but can't find anything of value - it seems...

---

### Post by steffen on 2007-02-10
Used the old installer (alternative), and was able to install. Don't know what kind of bug this is though. Any pointers on what to file to Launchpad?

---

