---
title: "Dual Boot XP on RAID 0 Ubuntu on USB drive"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by drabzz on 2007-11-23
I was going for a dual boot setup with XP installed on my RAID 0 array and with Ubuntu installed on a virgin 80Gb USB drive. I was using the 7.10 Live CD.

I kept getting GRUB error 21 issues, so I followed advice on these and various other Linux forums. I managed to get XP starting again by using a rescue CD and the FDISK /MBR command; which restores the Master Boot Record.

I tried restoring GRUB to the root of the USB drive, in accordance with advice from these forums. All my attempts met with frustration until I tried unplugging my RAID array, leaving the USB drive as my only HDD.

I chanced my arm and let the Live CD do its thing on auto install. My chance was met with success; Ubuntu is wholly installed on my USB drive!

I have set my BIOS to boot to the USB before the RAID array, and I control the USB with its manual power switch; off for XP, on for Ubuntu.

Forward Ubuntu!

---

