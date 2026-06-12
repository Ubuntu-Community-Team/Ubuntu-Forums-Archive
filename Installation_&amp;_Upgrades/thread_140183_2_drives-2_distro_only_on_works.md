---
title: "2 drives-2 distro only on works"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by eriefisher on 2006-03-05
Ubuntu is on a 30GB drive and was working perfectly. I installed a second drive(8GB) and loaded Mepis on it an installed Grub to the MBR of hda which is the 30GB drive. When I rebooted after the install there was no choice of operating systems and only mepis would load. I've tried to reinstall grub several diferent ways and times but no go. I want my Ubuntu back. In Mepis, I can mount hda and see all the Ubuntu files there and everything looks ok.

How can I get Ubuntu back on the Grub menu to load it? Nothing seems to do it.

eriefisher

---

### Post by drummer on 2006-03-05
Check the settings in your computer's BIOS and verify the device boot order, and put the hard drive you want to boot grub from ahead of the other hard drive. Grub might be installing to one drive, but the BIOS is booting the other, where there's a previous install of grub or something.

Another possibility is that the 'hiddenmenu' option is enabled in grub and you don't get to see the menu. To rectify this, fire up a terminal, "sudo nano /boot/grub/menu.lst" and find the line with just 'hiddenmenu' on it and comment it out (put a # at the start of the line). When this option is enabled, the grub menu isn't displayed on boot but instead has a one-line message telling you to hit ESC to show the menu, but it only lets you do this for 3 seconds i think. Once it's edited, CTL-O and CTL-X to save and quit.

---

