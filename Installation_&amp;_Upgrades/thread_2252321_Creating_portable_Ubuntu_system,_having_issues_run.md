---
title: "Creating portable Ubuntu system, having issues running on other systems"
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by jkarpan on 2014-11-11
Well, I've been playing around with this for a couple of days, and I've almost got my setup as complete as I'd like it. However, in some testing, I've noticed some issues.

I have Ubuntu 14.04 installed on an external hard drive - a Western Digital My Passport Ultra 1TB with USB 3.0. I have approximately 950GB partitioned as the ext4 filesystem so that I can perhaps use it for some small-time developing and classes and whatnot (Plug it into a computer and boot from USB, as the grub bootloader is also on the hard drive), and approximately 6GB for swap. The computer that was used to set up the hard drive with Ubuntu was a Lenovo X61 (With 4GB of ram, upgraded from stock 1GB, everything else is stock), which already has another copy of Ubuntu installed - both copies work perfectly fine on the device (I have a bit of experience with Ubuntu, so there's that). However, there's another computer that it doesn't seem to like. I'm running the hard drive, now, on an HP Media Center Edition m7640n (Running stock 2GB of ram, everything else is stock), and it *almost* works. When I say almost, here's what is actually happening:

1. I start up the computer and boot to the external hard drive with Ubuntu installed on it.
2. I select Ubuntu in grub and allow it to load.
3. I'm presented with the Ubuntu 14.04 user login screen. I enter my credentials and log in.
4. It logs in, however, only the mouse shows up on the screen. Roughly 5 minutes later, it locks up (Mouse is frozen, won't respond to keyboard commands, etc etc), or ends up in [this glitchy mess]("http://i.imgur.com/C7KMLUc.jpg"). Nautilus is not loaded at this point, even after waiting 5+ minutes.

I've had it only once, on a previous install attempt, actually load Nautilus, however, it still crashed as per usual within the 5 minutes.

But if I load this on the Lenovo, the device in which the OS was installed with, it loads perfectly fine, no issues whatsoever. I've even been able to update Ubuntu on it using the Software Updater. I'm wondering if perhaps there's some way I can debug it and post a log here to see exactly what is causing it to crash, so I can get it to run on other devices properly, as from what I can tell, it should be able to boot properly without issue on other devices, no matter what it was installed on. Any assistance would be muchly appreciated!

---

