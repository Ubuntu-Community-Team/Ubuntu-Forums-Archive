---
title: "Need help installing on a Toshiba 1805 series laptop"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by heavyPixel on 2006-09-01
I'm a new Ubuntu and linux user trying to install the Live CD on a Toshiba Satellite 1805-S274 laptop.

I've tried several burns of the disk, following the directions for burning the ISO found on the site.

I can boot to the pre-installation splash screen without a problem. However, when I try to proceed with an install I get the following error listed at the top of the screen:

Loading /csper/vmlinuz . . . . . . . . . isolinux: Disk error 28, AX = 4288, drive 82

In addition, the "Loading kernal" menu stalls out at 42% complete, and then displays an I/O error dialog reading "Error reading boot CD" with a reboot button.

I've tried disabling ACPI per recommendations in other threads with these two boot commands:
live acpi=off
live acpi=off noapic nolapic

But they don't seem to help.

I'm really eager to get this up and running, but as a linux newb I'm running out of idas :confused:

---

### Post by jeffdeloach on 2006-09-09
Sounds like a corrupt disc. You will probably have to burn a new one. Just a guess, I had similar problems in the past, and fixed it when I made a new disc.

---

### Post by rlcompton on 2007-10-19
Feisty installed with no problems after I reburned the iso at a slower speed. I have tried instlling Gutsy both by disc and by Update-Manager. No luck so far.

---

