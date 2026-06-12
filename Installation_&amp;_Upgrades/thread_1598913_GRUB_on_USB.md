---
title: "GRUB on USB"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by MagicalDean on 2010-10-17
Hello everyone,

Firstly, apologies for creating a thread entirely to solve my problems, but I've searched everywhere to no avail.

I have a laptop with two HDs, XP on one, and freshly installed Ubuntu 10.10 on the other. I want to avoid installing GRUB or similar, as most of the time I just use windows. I therefore decided to put GRUB on a USB, an option the alternate CD gave me.

For some reason, when I boot with the GRUB USB, nothing happens and my laptop boots normally into windows. I managed to get Ubuntu running off a USB stick, and the GRUB USB contains the files IO.SYS, COMMAND.COM and MSDOS.SYS, so I assume GRUB installed correctly.

Does anyone know what I need to do to get this to work?

---

### Post by C.S.Cameron on 2010-10-17
Is your BIOS set to boot the USB first?
Often BIOS will see a USB drive as just another hard drive and it needs to be set as first HDD to boot.

---

### Post by efflandt on 2010-10-17
Does your laptop actually have 2 physical hard drives, or is it one hard drive with separate partitions for Windows and Linux (don't be confused by Windows referring to D: as a drive)?  If it really has 2 hard drives, you could have put grub on the second drive and then press a key from the BIOS splash screen to select which drive to boot from.

How did you format and install grub to the USB?  It appears that it only has MS DOS files on it that you would see if you did **format /s** from DOS or Windows.  That would not show if grub is in its mbr.

Even if you set USB first in boot order in CMOS setup,  you might still need to press a key in the BIOS splash screen (sometimes F12 or Esc) to select to boot from that mbr. That may be a safety feature so you do not accidentally boot from other than the internal drive unless you intend to. The only virus I ever caught was spread by infected floppy disks many years ago if you accidentally left it in the drive and booted from it, and that could happen with CD/DVD from unknown source.

---

### Post by MagicalDean on 2010-10-18
The BIOS can definitely boot from USB, as that's how I installed Ubuntu.

My laptop definitely has two physical HDs. Is it easy to put GRUB on the second HD with the Alternate CD? I don't want to end up wiping XP off and leaving myself with nothing.In terms of putting

---

