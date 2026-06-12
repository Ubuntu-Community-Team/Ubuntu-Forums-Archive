---
title: "How to keep my Windows bootloader's backup?"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by applegrew on 2007-06-15
Actually I am contemplating to setup a dual boot system of Ubuntu Fiesty and Windows XP Home. I have currently the Windows installed.

My question is if later I want to remove Ubuntu completely then how will I replace Grub with my Windows bootloader so that I can boot into Windows?

....and will my laptop's Nvidia Geforce Go 7400 be enough to support the Desktop effects?

---

### Post by gauravp55 on 2007-06-15
U can remove Grub in 2 ways:
1> By using Recovery Console

[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

U need to use fixmbr command to repair your MBR once you restart your PC in Recovery Console Mode.

                  OR 

2 By creating a Windows 98 BOOT DISK:

Go to [www.bootdisk.com](www.bootdisk.com) and download Windows 98 SE OEM Boot Disk and simply install it on a formatted floppy disk. U can boot using that floppy disk and at the prompt u need to type:

A:>fdisk /mbr

Restart your Pc and you'll boot straight into windows.

---

### Post by applegrew on 2007-06-15
It seems I will have to use option 1 since I don't have floppy drive. Does this work without glitch? What about SuperGrub?

---

### Post by gauravp55 on 2007-06-15
It worked fine for me. Dunno about SuperGrub. Never used it before.

---

### Post by dreadlord_chris on 2007-06-15
> **applegrew said:**
> It seems I will have to use option 1 since I don't have floppy drive. Does this work without glitch? What about SuperGrub?

Supergrub should work too if you don't happen to have the Recovery Console installed. 
I'd recommend the Recovery Console first, Supergrub only if that isn't available.

And yes, it's a pretty basic function - should go without a hitch...

---

