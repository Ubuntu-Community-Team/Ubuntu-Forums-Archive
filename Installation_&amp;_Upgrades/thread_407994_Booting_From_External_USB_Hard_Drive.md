---
title: "Booting From External USB Hard Drive"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by SimonomiS on 2007-04-12
I have Ubuntu (6.06) installed onto a usb hard drive by using the Live CD, and now I want to, ideally, boot automatically from that.

There is no option in my BIOS to boot from usb, so I guess I need to use GRUB or another bootloader.

However, using Super Grub (The only one I could find where it's possible to put onto a floppy through Windows, I keep getting errors trying to get Grub onto floppy though the Live CD) it can't seem to find the usb harddrive at all. 

I can go through the Live CD and check the Ubuntu install, is there anyway to boot into it from there?

---

### Post by jakev383 on 2007-04-12
Look on the wiki - there's a link for a bootable floppy disk that allows you to bot from your USB drive after that.

---

### Post by SimonomiS on 2007-04-12
Do you mean one that I can create in Windows? Or are you talking about Grub?

Because it seems the LiveCD isn't detecting the floppy drive at all. It tells me /dev/fd0 doesn't exist.

---

### Post by jakev383 on 2007-04-13
> **SimonomiS said:**
> Do you mean one that I can create in Windows? Or are you talking about Grub?

Because it seems the LiveCD isn't detecting the floppy drive at all. It tells me /dev/fd0 doesn't exist.
You could create the disk in Windows.
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

