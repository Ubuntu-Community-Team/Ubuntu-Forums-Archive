---
title: "Installing Ubuntu From A Different Computer"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by bbnd on 2008-03-04
My friend gave me this junky laptop and I'm trying to revive it.  The computer has no input devices (floppy, CD or DVD drive) so I can not install from that.  It has one USB port and it looks like the BIOS will boot from it, but I haven't had any luck booting from a USB CD drive.  I was wondering if it's possible to install Ubuntu on a different laptop and then swap the harddrive.  Will this work?

thanks in advance,
-b

---

### Post by itix on 2008-03-04
Since the laptop is so crappy, I guess that it's usb 1.1 which explains why the external CD won't work. You can install it from an externas source like a pen drive or an ipod.

Here's a HOWTO: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by dstew on 2008-03-04
You can maybe do a network install using [unetbootin]("http://lubi.sourceforge.net/unetbootin.html"), which you can use from a USB pendrive. See the section "Using UNetbootin If You Don't Have an OS Installed".

---

### Post by bbnd on 2008-03-04
Awesome, thanks!  I'm working on it now.  So once I get it up and running from the pocket drive, is there anyway to install Ubuntu onto the internal harddrive?

-b

---

### Post by bbnd on 2008-03-04
> **dstew said:**
> You can maybe do a network install using [unetbootin]("http://lubi.sourceforge.net/unetbootin.html"), which you can use from a USB pendrive. See the section "Using UNetbootin If You Don't Have an OS Installed".

That looks like what I need to do, only problem is, Windows on this laptop was corrupted and I have no way of reinstalling it, hence why I'm trying to load Ubuntu.

-b

---

### Post by dstew on 2008-03-04
> only problem is, Windows on this laptop was corruptedThat's a problem? ;-) Seriously, you can make the bootable unetbootin pen drive on another computer. It's easiest if you can find an Ubuntu box to do it on.

---

### Post by bbnd on 2008-03-04
Ok, so I lied, it doesn't look like the BIOS recognizes the USB port.  Is there any way to load Ubuntu onto the IDE harddrive and then place it back in the laptop?  I have an external case for it and have tried loading it from another computer and then placing it back in the laptop, but I somehow I don't think the bootloader is getting installed correctly.  Does this seem like something that could work though?

-b

---

### Post by jken146 on 2008-03-04
This should work, but you need to be careful where you tell it to install the bootloader (GRUB).  It's pretty much the last thing you're asked in the GUI installer.  You need to put GRUB on the drive that will be going into the laptop.

---

### Post by dstew on 2008-03-04
Yes, you need to install grub onto the MBR of the extrenal drive that has your hard drive in it. If it only the second drive on the laptop where you are installing, a good guess would be to install grub to (hd1).

---

### Post by bbnd on 2008-03-04
I got it.  I found a desktop here at work and unplugged all of the harddrives.  I was able to install Ubuntu on the laptop harddrive with no problems and it's working now.  Thanks for the help everyone!

-b

---

### Post by gpilkay on 2008-03-04
Yes, please be careful when installing to any drive other then the primary or Master, as that's where Ubuntu puts the Grub by default.  You could possibly try to hook it up AS master, but I'm not sure that's possible with a laptop drive on a desktop system.

Depending on how old this laptop is, you may also want to try Xubuntu as it takes fewer resources.

---

