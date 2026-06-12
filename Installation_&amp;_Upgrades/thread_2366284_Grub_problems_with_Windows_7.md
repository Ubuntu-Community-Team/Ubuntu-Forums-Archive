---
title: "Grub problems with Windows 7"
date: 2017-07-15
forum: Installation &amp; Upgrades
---

### Post by neatrat on 2017-07-15
I had a system with a couple of Windows 7 (sda2 and sda2) and one Ubuntu(sda5) installation, but the grub had been corrupted and I was able to boot only into Windows.

I then created a live Ubuntu (I think it was a 16.04) on a usb, booted off it and ran the bootloader repair (GUI), reinstalling grub onto sda (didn't give partition number).

Rebooted the machine and landed up on the minimal bash-like line editing GNU GRUB screen. Read up forums, and again tried to reboot the live USB. Only this time, the same bash like screen returned with GRUB4DOS 0.4.6a scrawled on the top of the screen, under a message saying 'Booting find /menu.lst, /boot/grub/menu.lst, /grub/menu.lst. Jut below this was the old Minimal Bash-like line editing message and the Grub prompt.

I must add that my usb was NTFS formatted.

The BootInfo is here - [https://docs.google.com/document/d/1R_nTu9WRCJsBg49CFI0681_H6zNcUGm_QAt8K6UsI7w/edit?usp=drivesdk](https://docs.google.com/document/d/1R_nTu9WRCJsBg49CFI0681_H6zNcUGm_QAt8K6UsI7w/edit?usp=drivesdk)

Now what can I do?

Warmly,
Abhinav

---

