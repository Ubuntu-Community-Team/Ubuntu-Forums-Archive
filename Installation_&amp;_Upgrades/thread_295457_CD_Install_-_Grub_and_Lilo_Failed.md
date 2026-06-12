---
title: "CD Install - Grub and Lilo Failed"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by TomBailey on 2006-11-08
Hi

I am new to linux.  I have been running a low memory install on an old dell pc using the 6.1 386 alternate CD image.

The install seems to work fine right up until the end when it is unable to install grub or lilo.

Any suggestions?

From googling around it seems like having the live CD might be handy for fixing the problem, but there doesn't seem to be one available on any of the mirror sites.  Failing that creating a boot floppy would be a temporary fix, so any tips on creating one (form windows) would be helpful.

thanks.

---

### Post by catlett on 2006-11-08
> **TomBailey said:**
> Hi

I am new to linux.  I have been running a low memory install on an old dell pc using the 6.1 386 alternate CD image.

The install seems to work fine right up until the end when it is unable to install grub or lilo.

Any suggestions?

From googling around it seems like having the live CD might be handy for fixing the problem, but there doesn't seem to be one available on any of the mirror sites.  Failing that creating a boot floppy would be a temporary fix, so any tips on creating one (form windows) would be helpful.

thanks.
The live cd is the desktop installation disc. It boots to a live session and then you can install or you can stay in the live session. If you were going to use this mirror, this would be the selection for a live cd.
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/installcd.jpg[/IMG]

---

### Post by TomBailey on 2006-11-08
thanks, but I guess this isn't the solution for me as I couldn't run an install from the standard desktop disk.

Any other suggestions on how I could recover and get grub/lilo installed?

---

### Post by catlett on 2006-11-08
> **TomBailey said:**
> thanks, but I guess this isn't the solution for me as I couldn't run an install from the standard desktop disk.

Any other suggestions on how I could recover and get grub/lilo installed?

That's what I hate about the live cd install, it uses a ton of ram. Now that I thionk about it, I shouldn't have linked you to it because you stated you were on a low memory system.

You may want to try the GAG bootloader. [http://gag.sourceforge.net/](http://gag.sourceforge.net/) It is a small download. When you download it, unpack/unzip it and it will have a floppy disk image and a cd iso. You can burn it to an iso and boot or copy the floppy image to a floppy and boot. It may be worth a try.

---

