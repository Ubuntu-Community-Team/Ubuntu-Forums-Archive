---
title: "Installing Feisty Fawn on an external USB hard drive"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by Nosedog on 2007-05-23
I'm trying to install Feisty Fawn on an external 250 GB USB hard drive *without touching my main internal hard drive.* That means I want to install Ubuntu and the bootloader on the USB drive. I can set my BIOS to boot from USB drives.

I've installed Ubuntu and GRUB on the drive. I can reach the GRUB menu, but I can't start Ubuntu. It's saying something like "Failed to mount partition."

Apparently, I need to add a few USB-related modules to Ubuntu's boot configuration. I've seen the instructions located at [http://ubuntuforums.org/showthread.php?t=80811]("http://ubuntuforums.org/showthread.php?t=80811"), but they don't work anymore as they are out of date (the mkinitramfs stuff has been rearranged since then). I need up-to-date instructions!

(Feature request: Ubuntu's install program should correctly install Ubuntu to USB drives.)

---

