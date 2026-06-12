---
title: "USB drive boot problem"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by armitage374 on 2010-05-09
Ok, I'm going slowly insane(r) here. 
I've gotten through the distro upgrade on an AMD64 system no problems (except my WoW install under Wine going bonkers. Again. but nothing new there ;)). Hell, even my Samba and my Mediatomb runs smoothly. And ditto from my acer laptop btw. :)
 
Aside from the fact that I really DON'T like the purple bootscreen, there is one small fly in the ointment: One of my external USB drives (on the AMD system) fails during boot-up. 
 
Problem, I think, is that the entire system is on a powersaver cord (shuts off the externals automaticly when the power on the box is cut and I'm NOT sacrificing THAT with the powerprices being what they are around here) and the drive, an old philips 500 gb NTFS doesn't have enough time to spin up before the usb probe decides to punch out an error. That leads to me having to punch S for skip if I want to continue booting. This is mildly irritating and I was wondering if there was a way  to either ignore the error message or skip the probe during boot. The drive itself is in perfect health and shows up perfectly once Gnome is launched.

---

### Post by efflandt on 2010-05-09
If that happens before you even get the grub menu, it sounds like a BIOS issue.  Maybe try booting with the drive connected, go into CMOS setup, and remove USB from boot devices.  Then maybe it will not look for it.  The CMOS selection to do that might not even appear if a USB drive is not connected.

I have a somewhat different issue due to USB hard drive lag when actually trying to boot from USB on Dell laptops.  I have to go into CMOS setup and change something (usually just the boot order of floppy and CD/DVD), just so it can save and reboot with the USB hd already spun up.  If I go into CMOS and change nothing, it resumes booting Windows from the internal hard drive instead of resetting and starting boot from scratch.

I don't have that issue with my HP desktop or Toshiba laptop.  They find the USB hard drive fine.

---

