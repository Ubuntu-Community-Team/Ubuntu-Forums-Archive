---
title: "Boot Grub from usb"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by LowSky on 2007-07-19
Is there a way so i can boot from usb, so that I can use grub to pick which hard drive to boot from

I have Windows on a SATA drive and Ubuntu on an  IDE drive.

I dont want to put both OSes on the same drive. Basically want it so that if the USB isn't plug in it boots directly to the SATA drive (MB's primary set up)

What would I have to do to load Grub to a USB drive then be able to pick which drive I want to use... is this even possible?

Im getting tired of switching options in my bios or unpluging cables. And I want both drives to be seen so I can open files or transfer things like music and pictures between OSes.


If I cant do that is it possible to set up Grub for two diferent drives. Basically have Grub boot then pick which OS even if the Os is on another HD

---

### Post by LowSky on 2007-07-19
Bump?

---

### Post by rbmorse on 2007-07-19
I dunno about the USB part but as for the last question, that is exactly what GRUB is supposed to do and the defaults during installation should have set that up. 

You don't mention what the other operating system is, but if it is Windows XP or earlier normally you would start by installing and configuring Windows on the machine, then installing your linux(es).  If VISTA is in the mix I'm gonna bail because I haven't used it, but I do know from casual reading that VISTA uses a different boot loader scheme than previous versions and I don't know how to integrate than into GRUB. 

When the Ubuntu installer sets up GRUB it should detect the Windows installation(s) and create the appropriate boot menu entries. It doesn't matter which drives or partitions the O/S are installed into as long as they can be detected by the Ubuntu installer.  When the machine boots you are presented with a list of installed operating systems (up to 7 by default but this can be changed) and you use the arrow keys to select the desired O/S to boot and hit enter. 

If you're not seeing this you have to setup GRUB again. Not terribly difficult. There are a number of good guides already here, or ask if you need help finding one that makes sense to you.

---

### Post by MQMike on 2007-07-28
Low Sky,

Sometimes – not always – it takes a bit of effort to configure GRUB to handle a mixture of IDE and SATA hard drives (there are seldom big issues if you have all SATAs or all IDEs).  But not a terribly big deal as many people have done it (google on it).  See the references below for how to do that – you’d be installing GRUB to the MBR of your Windows drive, and make the Windows drive the first (BIOS-) bootable hard drive on your system.

That said, if you want to play around and learn some stuff, perhaps you could put your GRUB bootloader on a thumb drive, or put Super Grub Disk on the thumb drive or a bootable CD, or put both your own custom GRUB booting menu and SGD on a thumb drive.  Plug in your thumb drive, turn on your PC, up comes your boot menu choices from your thumb drive, etc.  This little project might go quickly and smoothly or it might take a bit of effort (basically knowing which drives are which and what GRUB calls them, the (hdx) numbering).

Here’s some options, should the mood strike you to dig into this:

Make a bootable Super Grub Disk CD:
Super Grub Disk:   [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
(download versions of SGD)

How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(general GRUB methods for everyday use)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
(the classic GRUB reference for doing many neat things)

---

