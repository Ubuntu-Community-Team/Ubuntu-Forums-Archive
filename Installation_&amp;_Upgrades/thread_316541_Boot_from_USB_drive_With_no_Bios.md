---
title: "Boot from USB drive? With no Bios?"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by swarm on 2006-12-10
I have a laptop (Toshiba Satellite S501-5105) that does not have a bios. It is Legacy-Free, and would be controlled via windows.. Te IDE controller on my laptop went out, and now it does not recognize the internal hard drive - I can boot off the live CD with no issue, but it still does not recognize the internal drive.

I just purchased an external USB hard drive, and would like to use it as my normal hard drive. I have no way to boot from the USB drive, but I was wondering if there was a way I could boot from CD, and have it redirect to the hard drive, or even boot with a thumb drive initially..

Any ideas, guys?

Tanks for your help!
Eric

---

### Post by ciscosurfer on 2006-12-10
No BIOS?  What??? I've never heard of such a thing!

Try hitting your F keys (F1 through F12 to enter your BIOS...sometimes DEL or ESC will enter your BIOS...it depends on the manufacturer)

---

### Post by IanW on 2006-12-11
From the first entry when Googling "Toshiba Satellite S501-5105 bios":-

> The final method discussed is for the following Toshiba models:

    Satellite 5005-S504, 5005-S507, 5005-S508, 5105-S607, 5105-S608, 5105-S501, 5105-S701, 5105-S502, 5105-S702, 5105-S901, 5205-S503, 5205-S703, 5205-S504, and 5205-S704

These are "legacy-free" models, and they do not incorporate a BIOS Setup program in the motherboard ROM. The only way to run BIOS Setup is using a Windows-based BIOS Setup utility called HWSetup. The HWSetup utility comes preinstalled on these Toshiba models, and it is also contained in the Toshiba Utilities package for these models, which can be downloaded from the Toshiba support Web site. To run HWSetup, open the Control Panel and double-click the HWSetup program. HWSetup provides a graphical front end for modifying BIOS settings. Note that if you change any settings, you may be required to restart the system.

In other words, you seem to be screwed. :(

IDEA: Unless you can get the HWSetup program running under wine in the LiveCD environment (but I very much doubt it).

---

### Post by ciscosurfer on 2006-12-11
> **IanW said:**
> From the first entry when Googling "Toshiba Satellite S501-5105 bios":-



In other words, you seem to be screwed. :(

IDEA: Unless you can get the HWSetup program running under wine in the LiveCD environment (but I very much doubt it).Without straying too much off-topic, what does *not* having a BIOS accomplish?  I can certainly see what not having one accomplishes!

---

### Post by Dulwithe on 2006-12-12
Hold and/or press F12 as your computer boots and you will be able to use the arrow keys to move between boot options.

It sounds like your HDD might be fried, or it could be a motherboard or connection problem.  Take out (or have someone take out) your HDD, test it, if it works you will likely have problems booting from anything.  If it doesn't work, buy yourself a cheap HDD.

If your cptr recognizes the CD, I expect it isn't the IDE controller that is the problem.

Also, if it is true that the IDE recognizes your CD and not HDD, you can install Ubuntu on a USB drive and install GRUB on a floppy disk or CD, so you should be able to get it working like you suggest.  Just do some more googling.

Or try the alternate install CD, aim to USB for installation, say "NO" when asked to install grub, then dictate where Grub should be installed.  Shouldn't be too difficult.

D, TDS

---

### Post by LamaZ on 2007-01-30
I have a Satellite 5205-s703.  To boot strait into a CD (the internal one), reboot and hold down the "C" key.

-LamaZ

---

### Post by cw7585 on 2007-02-10
You're actually not (yet) screwed. I have a machine that does what you're describing -the IDE controller "went out" and lacks a "boot from USB" option, so a CD-ROM does a brief 20 sercond boot sequence before turning things over to the USB external drive to continue loading into Gnome. 

There's a thread which discusses this method, here:

[http://ubuntuforums.org/showthread.php?t=266068&highlight=usb+bios](http://ubuntuforums.org/showthread.php?t=266068&highlight=usb+bios)

There's also a Howto linked in that thread which gives further details on baking such a boot CD. Hope it's a help!

---

