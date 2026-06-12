---
title: "anyway to do this without uninstalling"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by MTMuir on 2009-12-01
I'm Getting a new computer with in the next two weeks, and I would like to take ubuntu with me. I have ubuntu installed on my external hard drive, and I want to just unplug that plug it in but I need a boot loader for vista, any idea how to install one with out uninstalling  and reinstalling ubuntu from my exteral hard drive.

thank for your time

---

### Post by MTMuir on 2009-12-01
and one reason why i don't just re install is because I let a friend barrow my disk and he lost them. added to that for some reason any disk I make get messed up. ( part of the reason why i'm getting a new computer, the disk drive is not working right.)

---

### Post by darkod on 2009-12-01
OK, so you have your ubuntu installed on external usb hdd? How are you booting it right now? Is the BIOS set to boot from usb hdd first?
In that case the bootloader (grub1 or grub2) is on your external hdd. You will just need to plug it into your new computer, set the BIOS to boot from usb hdd as first choice, and update the grub menu with the OS that comes on your new computer internal drive(s).

---

