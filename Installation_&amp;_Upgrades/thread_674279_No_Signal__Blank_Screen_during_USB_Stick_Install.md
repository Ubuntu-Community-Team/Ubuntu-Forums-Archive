---
title: "No Signal / Blank Screen during USB Stick Install"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by onezero on 2008-01-21
Hello all.  First things first, I've spent quite a bit of time searching all of the different boards here and can't really find anything specific to my problem, so I'm making yet another USB drive install post.

I followed the tutorial at pendrivelinux.com and got the USB stick to boot wonderfully.  The problem comes after I choose one of the boot options, persistent, live, safe graphics, OEM install, they all do the same thing.  Once I choose one of those options the progress bar will load from 0% to 100% and sit for about a minute as everything is copied from my drive into memory.  Once that is finished, the screen will go black for a few seconds, followed by my LCD monitor saying "No Signal" and going into standby mode.  At this point, I've waited up to a half hour figuring maybe it was just copying some more things from the USB stick, but activity stops after about a minute and it just sits with no signal.

Has anyone had a problem like this before?  I don't think there's anything wrong with my USB stick, I'm thinking it has to do with my video card or something.  Here are my system specs.

ISO I copied the files from: 7.10, amd64

CPU: Athlon 64 X2 5200+
Memory: 2GB
Graphics: GeForce 8600 GT
USB stick: SanDisk Cruzer 1GB

Any help is greatly appreciated.  Thank you for your time!

---

### Post by Pumalite on 2008-01-21
What driver did you install for your graphics card?

---

### Post by onezero on 2008-01-21
I'm not sure you read my post correctly, eh its not really clear. :)  I can't even get to the point of installing.  It goes blank and I get "no signal" after the kernel loading bar.

---

### Post by Sergeantfour on 2008-01-21
Same thing happens to me during a disk install.  I've looked around and tried a bunch of stuff but I can't fix it either.

---

### Post by onezero on 2008-01-21
> **Sergeantfour said:**
> Same thing happens to me during a disk install.  I've looked around and tried a bunch of stuff but I can't fix it either.

Don't squash my hopes! Haha :)

---

### Post by Sergeantfour on 2008-01-21
Don't despair!  I have a lot of faith in the Unbuntumasters that help for fun.

---

### Post by onezero on 2008-01-21
Update: I forgot to mention, booting from a LiveCD on this machine works just fine.

---

### Post by Pumalite on 2008-01-21
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
I would recommend disconnecting all internal drives during the installation.

---

### Post by onezero on 2008-01-21
Thats the guide I used Puma.  Everything works fine as far as booting from the USB and whatnot.

I fixed the problem though, for anyone out there with a similar one.

Press F6 when you get to the boot screen and remove "splash" from the line, then boot.  When the GDM login window finally displays, if your screen goes blank, hit CTRL+ALT+F1, wait a few seconds, then hit CTRL+ALT+F7 and you should now be looking at the GDM login screen again, but it'll stay there this time.

Note that when you do install Ubuntu, you'll also have to remove "splash" from the boot options for GRUB otherwise it'll do this all over again.

---

