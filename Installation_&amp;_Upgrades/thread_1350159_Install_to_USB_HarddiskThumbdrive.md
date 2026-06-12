---
title: "Install to USB Harddisk/Thumbdrive"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by JasonInferno on 2009-12-09
Hey, me again.

I've always wanted to use Xubuntu, and I know it can be installed on removable media, but have no way to get it installed. I haven't got any spare CD-Rs left, so burning a CD and installing it to my media isn't an option.

I know that Pendrivelinux tells you how to install most distros to a thumbdrive, but it only gives a guide on how to do so via Windows and Macintosh. Right now, I'm running Ubuntu Jaunty, so last time I checked, what was displayed won't work on my system.

Can anybody give me a way to install a full version (not a LiveCD/USB) of Xubuntu to a USB harddrive/flash drive without using a CD?

---

### Post by wilee-nilee on 2009-12-09
In system-administration is usb startup disc creator, use a ISO to load it and set the persistent with the slider and it will read the ISO and keep updates and installs.

---

### Post by JasonInferno on 2009-12-09
Yeah, but that's when it's been installed to a disc or on a live system. I can't create a LiveUSB or LiveCD, nor can I install it to my harddisk. I'm running Jaunty right now, so I can only install the discs that I have available. And I don't have a Xubuntu disc.

**Edit**: Whoops, I forgot to read the part about loading the .ISO file instead of the CD drive. I never noticed that part. Thanks for the help.

---

### Post by JasonInferno on 2009-12-09
I just realised that doing what you said will install a live version to my harddisk, not a full installation. So yeah, that method is out of the question.

---

### Post by MaindotC on 2009-12-09
You could start a VM using the 9.10 image, enable USB support, plug in your USB drive, and tell the installer to put it on your attached usb drive.  I did this on a 16 gigger.  It's going to kill the read/write on your drive very quickly but it will definitely last a few months.  The only thing is when you're done installing it to your usb drive, you have to actually boot the host machine from your usb drive.  To my knowledge, VBox does not allow booting a VM from a usb.

---

### Post by wilee-nilee on 2009-12-09
Sorry missed the full install bit. So is it a usb flash HD or a regular usb HD?

It is a little confusing as to what your trying to do a full install to, could you give the device description. I know you looked at the pendrive but the site has a lot of stuff to look at did you get here.
[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

---

### Post by wilee-nilee on 2009-12-09
If you want to check out Xubuntu you can install within Ubuntu and choose that desktop at log-in, you don't have to have a separate HD and a USB HD will run slow anyway. If you want to install it in Ubuntu run in the terminal.
sudo apt-get install xubuntu-desktop.

---

### Post by MaindotC on 2009-12-09
> **wilee-nilee said:**
> Sorry missed the full install bit. So is it a usb flash HD or a regular usb HD?

The thread is titled "Thumbdrive" so I think it's safe to say it's a flash hd, not that it makes a bit of difference...

---

