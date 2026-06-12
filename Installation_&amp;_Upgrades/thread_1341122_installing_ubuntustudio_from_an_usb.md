---
title: "installing ubuntustudio from an usb"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by herbert tamayo on 2009-11-29
Hi, I recently finished to download ubuntu studio 9.10 iso image file, I need to install on a laptop that does not have CD/DVD drive, so using unetbootin I've installed the iso file in my usb drive. So the problem is that in the installation part ubuntu studio always try to seek a CD drive as the installation source, also trying the expert install only it gives me the option of use the repos online, obviously I don't want to download it again.

now, my question is:
is there any parameter/command in the installation that avoid to seek the DVD drive and use my usb as the installation source media?

thanks a lot

---

### Post by nitstorm on 2009-11-29
did u try changing the boot order in the bios?

---

### Post by herbert tamayo on 2009-11-29
yes, in fact, I can boot from my usb, the problem is the ubuntu studio installer that is always seeking the CD Drive to load the install files, is there a way to tell the installer that use the pendrive instead of the cd drive?

---

### Post by nitstorm on 2009-11-29
sorry mate no idea there, but some one else should have an idea. sorry newbie here too, but will remain subscribed to this coz i am installing ubuntustudio 9.10 myself in a few days, hope this gets solved, cheers!

---

### Post by phillw on 2009-11-29
> **herbert tamayo said:**
> yes, in fact, I can boot from my usb, the problem is the ubuntu studio installer that is always seeking the CD Drive to load the install files, is there a way to tell the installer that use the pendrive instead of the cd drive?

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)  have howto put iso's etc onto pendrives, if ubuntu studio isn't specifically mentioned.

Or, you can follow the unetbootin path - as detailed here - [http://answers.yahoo.com/question/index?qid=20090819092054AABqmXf](http://answers.yahoo.com/question/index?qid=20090819092054AABqmXf) 

Regards,

phill.

---

### Post by darkod on 2009-11-29
What you could also try is disable the unetbootin menu and allow the ubuntu menu to show. Not sure about Ubuntu Studio, but on Ubuntu you can do that by opening your usb stick after creating it with unetbootin and:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the isolinux folder rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename whole folder isolinux to syslinux

That should allow the main ubuntu menu to show.

---

### Post by Joomla12 on 2009-11-29
Sorry to do this but I have the same exact problem. I can boot from the USB stick just fine but when the installation begins, it says that it was unable to mount the installation CD.

---

