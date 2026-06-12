---
title: "make persistent bootable usb disk from existing bootable internal disk"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by pdonner on 2008-04-22
If I already have a bootable internal IDE ubuntu disk and I want to move it to an external USB enclosure and boot it on a separate machine (with persistence), can someone tell what I need to do to make this work?

Thanks.

---

### Post by cwelch on 2008-04-30
I don't remember if it manages the bootloader or what, but go look for PING (Ping Is Not Ghost) and burn the ISO to a disk and just ghost it if you're moving it to a new HDD. If not, just get an enclosure and slap it in there. I have often taken my 7.04 and 7.10 out of my laptop and put a different drive in for something, then put the original drive into a usb enclosure and rebooted and it saw the loader for the USB drive first since it was in my boot dev list on top. Give that a shot. If you start the computer cold though, you'll likely have to reset it during the bios/post so that the usb drive will be seen to load from. My laptop doesn't init and spin the usb one fast enough for a cold boot to recognize it, but if I reboot it during the grub screen for my internal drive, it will work fine and hasn't caused any problems. Otherwise if you're using a USB FLASH disk, just use PING to ghost it back to that device. I've sucessfully loaded a clean 7.04 and 7.10 on my 4GB thumb drive. But not Xp or 2K/2K3.. Score: Linux 300 - Windows 0!

---

