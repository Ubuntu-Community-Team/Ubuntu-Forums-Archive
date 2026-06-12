---
title: "Upgrade Manager and dual boot glitch"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by incognito on 2006-06-12
Hi:

I just used Upgrade Manager to jump from Breezy to Dapper. I had Breezy and XP dually installed on the same IDE drive as follows:

/dev/hda1 NTFS XP
/dev/hda2 ext Breezy -> Dapper
/dev/hda3 swap 2 GB
/dev/hda4 5 GB virtual FAT
free space 3.9 GB

There were no errors during the Dapper upgrade, but on restart only Ubuntu 386 kernel options appear on the boot menu and the old XP option at the bottom is missing. System/Administration/Disks shows the partitions to be intact. Did Update Manager corrupt the MBR? How do I get XP back? Ubuntu forum search and Google did not yield an exactly matching solution so I thought I would ask for help first to avoid long hours of restoring. Many thanks in advance.

incognito

---

### Post by Joeb on 2006-06-12
If you edit /boot/grub/menu.lst as root (use sudo), you can manually add your Windows session back in.  Lines beginning with a # are comments and towards the top is an example for Windows 9x.  Since your XP is on /dev/hda1 it should be the same (changing your description to Windows XP).  You should be able to add the lines to the end of the menu.lst and reboot to see if it worked.

---

### Post by incognito on 2006-06-14
Hi:

Thanks, Joeb.

The grub conf file already had these changes for XP which is why I was suspecting the MBR had been revised. Instead, since I had so many kernel updates listed the selection screen the Windows XP option had just dropped out of the scroll box whose listings can extend beyond the rectangle screen display.

Ubuntu and its forums are great. I hope this might help someone else.

incognito

---

