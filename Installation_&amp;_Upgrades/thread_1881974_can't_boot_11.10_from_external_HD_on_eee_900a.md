---
title: "can't boot 11.10 from external HD on eee 900a"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by drcrash on 2011-11-16
I'm running Ubuntu 10.04 on an ASUS eee pc 900a and trying to install Kubuntu 11.10 on an external hard drive, and boot off of it.  I can install to the external drive but not boot off it.

I think I had the same problem with regular Ubuntu a version back, and never got it to boot off the external drive.  (And gave up.)

Booting seems to go fine until I get to grub, which defaults to booting the first option, a 2.6 kernel, which boots my old system.  I can instead scroll down and at the very bottom I find a 3.0.0 kernel ("(on /dev/sdb1)") which I assume is the new system I want to boot on the external drive, but when I pick it, I get errors, with something "not found." and saying that I need to load the kernel first.

I can't actually read all of what's being said up to that point, because my screen is not displaying properly, and the beginnings of lines are off the left edge of the screen.  (When my old system boots, it sorts things out properly and the display is fine.  That's on an external monitor---I'd guess it would display fine on the built-in screen, but that's physically broken.)

Grub says it's "1.98-1ubuntu12" which I guess is the old grub on the internal (SSD) drive.  (I got the impression somewhere that 11.0 uses grub 1.99, so I tentatively infer that the boot process is not finding the grub on the external HD.)

BTW, I have the external drive plugged in to the left-side USB port, which the 901a can boot off of.  (That's where I plugged in the CD-ROM to run the kubuntu-11.10-desktop-i386  install disk.)  I have also set the BIOS device priority to look for an external device first and the internal drive last.  I don't know why it doesn't find the new install on the external disk and boot that.

I tried doing a "sudo grub-update" in a window on the running old install,  but it doesn't seem to have helped.  (I guess I wouldn't mind if I used the old grub on the internal SSD to boot the new install on the external HD, but I guess that doesn't work.)

For what it's worth, I did the simplest possible install, telling it to use the whole external disk for kubuntu.  (I'd tried it differently first, putting it in a new partition, and that didn't work.  I was wondering if my old install of regular Ubuntu that never booted was messing things up, so I gave this install the whole disk.)

Any help would be much appreciated.

---

### Post by drcrash on 2011-11-16
After getting a different monitor so I could see the boot stuff, I realized I'd missed a BIOS option, which I think I got right last time this failed, and fixing it doesn't fix the problem.

There's an option to specify hard drive order as well as device type order.  The BIOS does see the external hard drive as a hard drive (not just an external device), so I made that first and the internal drive last (second).

Now when it fails I get a "file not found" error and a grub rescue prompt, which I don't know what to do with.  (I suspect that's what happened last time I tried to install the previous stable version of regular Ubuntu;  either way it's what's happening now with Kubuntu 11.10.)

---

