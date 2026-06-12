---
title: "BIOS trouble"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by thomsmells on 2012-01-07
So I'm currently trying to install Lubuntu on my old desktop (Advent t9101) through a flash drive, only I can't get the USB to boot. I've tried it on my laptop and it works fine, so it's an issue with the boot sequence.

These are the boot sequence options I've got in BIOS:

Floppy
LS120
HDD-0
SCSI
CDROM
HDD-1
HDD-2
HDD-3
ZIP100
USB-FDD
CARD-READER
USB-HDD
LAN
Disabled

I've tried all the options with 'USB' in the title, and it doesn't seem to pick it up, any ideas?

---

### Post by ottosykora on 2012-01-07
usb hdd should do, on some older computer the usb-fdd was helpful, but 

Q: is your usb flash device bootable at all? Does it boot from it on other machine?

---

### Post by Rex Bouwense on 2012-01-07
Some computers recognize the flash drive as an additional hard drive.  Look at the BIOS without the flash drive inserted.  Then look at with the flash drive inserted.  See if there is an additional hard drive detected.  If there is, that is your hard drive.  Then again some computers will not boot from a flash drive.  You always have the option of making a bootable CD and use your CD drive to install.

---

### Post by thomsmells on 2012-01-07
Like I said I tried it from my laptop and it booted fine, just not from the desktop.

Does it matter which order you put it in? There's a three part sequence (boot 1, boot 2, boot3) and then a default, I tried the usb settings on all three, does it have to be the first one?

Also tried it with and without, all the same options were there.

---

### Post by darkod on 2012-01-07
If there is an option during boot to enter a boot menu with F10, F12 or similar, try that too.

Plug in the stick. Power on the desktop, press the required button to enter the boot menu. Wait a little bit in case it needs to detect the stick better.

Try with USB-HDD, usually sticks go under that. Sometimes in the boot menu it will even say like Kingston Data Traveller, etc, the brand/model of the stick.

This option to enter a boot menu is avalable in most recent boards and overrides the boot settings in BIOS. For example, you can keep your HDD as first device in bios always, and use the boot menu for occasional boot from cd-rom, usb, etc.

---

### Post by larjan on 2012-01-07
With some older motherboards, you must change usb emulation for it to boot. First, enter your bios, find "advanced" or "advanced settings" tab. There should be something that says, usb config or settings, find "usb emulation". This is usually set to "auto" buy default, change it to hdd. Go to boot order, your usb drive should now show as a hdd. Make it the first boot device. if your flash drive is bootable, this should do the trick.

---

### Post by thomsmells on 2012-01-07
There is a boot menu, but it's blooming password protected, so I have no idea how to get into it.

As for advanced options, I can't find any usb emulation settings.

---

### Post by larjan on 2012-01-07
Reset your bios, either with the jumper or by removing the battery for 30 seconds or so ( in both cases, with the power disconnected). If this does not remove the password protection, you will have to get the default password from the computer or bios maker. Alot of proprietary boards do not have advanced settings in there bios. most after market ones, even old ones do. bottom line, without seeing what you have, as far as bios settings, I'm not sure what to tell you to do. If your bios cannot be made to see your flash drive as a hdd, you will not be able to boot from it. The only thing I can think of at this point is, see what bios and version you are using, and see if you can find info online regarding settings. Also, see if there is a newer version with more capabilities. sorry I couldn't be of more help. If anything else comes to mind, I will post it back here.

---

