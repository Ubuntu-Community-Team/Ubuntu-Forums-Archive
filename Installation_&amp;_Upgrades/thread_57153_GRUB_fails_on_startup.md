---
title: "GRUB fails on startup"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by mortenalver on 2005-08-15
Hi,

I just tried Ubuntu 5.04 for the first time a couple of days ago, and it looks very pleasant and good to work with. 

The computer is a brand new Dell Latitude D810. It came with Windows XP pro SP2 preinstalled, and I used the Ubuntu installer to reduce the size of the NTFS partition. Then I installed Ubuntu with a swap + a root partition. After install, I could run both WinXP and Ubuntu from the boot loader (grub). The installer did very well, setting up everything correctly, as far as I could see (haven't checked Wi-fi).

This worked trough more or less 3 startups of each OS. I installed software, and installled software updates (with the automatic updater, which looks very professional, by the way), but I don't think I've messed with the boot/startup stuff.

Today at startup, I could briefly see the message "Loading Grub (...)" or whatever, before the screen went blank, and the machine rebooted (showing the Dell logo). This repeated in a seemingly endless loop.

I managed to restore the system by booting in rescue mode from the Ubuntu CD, and running "grub-install /dev/sda". However, I expect this to happen again, and I am not very comfortable with the situation. Has anyone seen anything similar, and does anyone have any good advice to help avoid this happening?


Morten

---

### Post by mortenalver on 2005-08-16
[QUOTE=mortenalver]Hi,
I managed to restore the system by booting in rescue mode from the Ubuntu CD, and running "grub-install /dev/sda". However, I expect this to happen again, and I am not very comfortable with the situation. Has anyone seen anything similar, and does anyone have any good advice to help avoid this happening?
[/QUOTE]

Just a followup: it happened again. I've only booted the computer once, in Windows XP, since fixing it with the rescue CD. It's apparent that this problem isn't going away. Perhaps I should try installing Lilo?

Morten

---

