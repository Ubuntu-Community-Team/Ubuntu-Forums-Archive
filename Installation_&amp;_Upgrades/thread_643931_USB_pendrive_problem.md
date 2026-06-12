---
title: "USB pendrive problem"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by dykesy61 on 2007-12-18
I am running 7.10 on my desktop but want to be able to use a pendrive to transfer my files, easily, round the other computers I use.
I have set up a system on the pendrive as per Ububtu 7.10 USB Installation Tutorial.
But I don't have an option in my BIOS to boot from a USB drive - I have a USB-CDRom, a USB-Floppy, even a ZIP-Drive.
So I need to amend the Grub Loader, I believe, to allow it to boot from the USB drive.
Can you tell me what command I need to add into the loader to do so?
Or is there another way?
Any help would be great - thanks

---

### Post by DarkN00b on 2007-12-18
This is also of interest to me. My CD/DVD-rom drive is out of alignment (don't ask) and I need to boot from my USB stick. I could netboot but that is a lot of work I'd like to avoid if possible.

This should be a matter of editing GRUB to hand off the boot process to a USB device, right?

---

### Post by lswest on 2007-12-18
actually i believe if there is no option in your bios (or boot menu of the bios) for a usb/pendrive then you probably cant boot to it.  however, the USB drive may appear under hard drives, so you'd have to change the order of the drives so the USB stick is selected first.  It's what happens on my PC.

---

### Post by DarkN00b on 2007-12-18
> **lswest said:**
> actually i believe if there is no option in your bios (or boot menu of the bios) for a usb/pendrive then you probably cant boot to it.  however, the USB drive may appear under hard drives, so you'd have to change the order of the drives so the USB stick is selected first.  It's what happens on my PC.

Thanks for your reply.

That's what I'm talking about. I want to point GRUB to my pendrive as the boot device. My BIOS doesn't have the option to boot from USB even though it is only about 2 years old. t should boot just fine if GRUB is configured correctly though. I'm still searching the forums and Google for an answer. I'll find it -- I tend to be persistent. :D

---

### Post by dykesy61 on 2007-12-18
I set it to USB-ZIP and it recognises the drive but says its an invalid system disk.
I used the following link, to the letter I thought, but it doesn't work.
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
any thoughts anyone?

---

### Post by lswest on 2007-12-18
have you checked (with the USB drive plugged in) if it shows up under hard drives? because then you have to (in bios) change the order of hard drives.  otherwise you probably won't be able to "point" GRUB to the USB.  Also, make sure the USB stick has been made bootable, otherwise it won't boot no matter what.  (usually the usb drive option only appears in the BIOS after a bootable drive has been detected)

---

### Post by dykesy61 on 2007-12-18
thanks - yes, it does appear as a drive, and yes it is bootable, according to partition editor.
but it still thinks its not a proper system disk - no idea why!
I have contacted Pendrtive to ask them too.
Thanks for replying.

---

### Post by DarkN00b on 2007-12-19
It may be necessary to format the drive to ext3.

---

