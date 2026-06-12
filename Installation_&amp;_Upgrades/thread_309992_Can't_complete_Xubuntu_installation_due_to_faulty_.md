---
title: "Can't complete Xubuntu installation due to faulty cd-rom"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by godrox on 2006-11-30
Someone gave me an old Toshiba Tecra 8000 laptop (PII, 128 memory, 6 GB HDD), so I promptly removed Windows 98 and have been trying to install Xubuntu for days now. The problem is that the cd-rom doesn't work very well and stops reading CDs at random times. I can't get it to read the Xubuntu installation CD long enough to complete the installation. I've tried various other methods of installation, such as booting from USB (not supported by the BIOS and even with third-party software like Smart Boot Manager) and floppy (found out the external floppy drive doesn't work at all). I have a PCMCIA 10/100 ethernet card and tried to find an easy way of doing a network install, but they all seem pretty complicated for someone like me.

So, I tried installing Xubuntu from CD again this morning and it got most of the way through the installation but quit at 85% of "Select and Install Software" stage, which is the furthest its ever gotten. (I'm using the Xubuntu 6.10 Alternate CD with text install option. ALT+F4 revealed it stopped after "thunderbird-locale-en-gb ttf-opensymbol wamerican ubritish.") I thought maybe this would be enough and I could finish the software installation by other means since the base system installed successfully, but apparently not. I boot to "GRUB error 15."

Is there any way I can pick up the installation where it left off since it never got this far before?

---

### Post by godrox on 2006-11-30
Well, I got it worked out myself. I was able to successfully complete an "command line installation" from the alternate CD. From there, I enabled the universe sources and commented out the CD-ROM sources and ran "sudo apt-get install xubuntu-desktop" and everything ran fine from there.

---

