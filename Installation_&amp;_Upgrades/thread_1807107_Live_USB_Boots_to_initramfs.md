---
title: "Live USB Boots to initramfs"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by aaaantoine on 2011-07-18
So I tried setting up an 11.04 Live USB image on my flash stick to try out and/or install Ubuntu on my laptop.  But instead of booting to the live desktop, I get a bunch of errors and an initramfs prompt (funny side note: if you type exit there you cause a kernel panic).

I looked into the problem a bit and found this thread.
[http://www.linuxquestions.org/questions/linux-newbie-8/busybox-shows-up-with-initramfs-prompt-on-usb-installed-ubuntu-8-10-and-8-04-a-679684/](http://www.linuxquestions.org/questions/linux-newbie-8/busybox-shows-up-with-initramfs-prompt-on-usb-installed-ubuntu-8-10-and-8-04-a-679684/)

Of all the solutions, this one seems to line up best with my problem.  I'm making the Live USB from my desktop and trying to run it on my laptop.  On my desktop the device exists as /dev/sr0, but I see no sign of that in initramfs.

So how do I tell the device to boot by label or UUID instead of by device?

Edit: Strange, I get the same error (/dev/sr0 not found) on my desktop as well.

---

