---
title: "Trying to install Ubuntu, unable to unmount ISO file"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by Greenwick on 2014-12-13
I tried to install Ubuntu as a dual boot with Windows XP last year. It didn't work. Now I am trying to install Ubuntu without a dual boot, and just completely erase Windows XP. I get through most of the install okay, but when it comes to deleting Windows, a notice shows up saying that an ISO file is mounted, and needs to be unmounted. I've followed directions for unmounting things, and now I don't see anything else to unmount.
 I've also tried to delete the previous attempt to install Ubuntu, but so far no luck.

I'm familiar enough with Ubuntu that I can do some trouble-shooting, but now I'm not even sure where to look.

---

### Post by agillator on 2014-12-13
As I understand your situation you are simply trying to install ubuntu as the only OS and wipe/delete/lose everything else, i.e. start fresh. Correct? I also assume you are trying to install from a CD/DVD installation disk. Correct?

---

### Post by ibjsb4 on 2014-12-13
You may also want to post your computer specs (cpu, ram, video).

---

### Post by QIII on 2014-12-13
Hello!

Are you trying to install Ubuntu using Wubi?  That is, are you inserting the installation medium while Windows is running?

---

### Post by Greenwick on 2014-12-13
I originally tried with a USB stick and had no luck. This recent attempt, I have been using an iso file and then using Virtual Clone Drive instead. I am considering trying to install with a USB stick again, though.

Here are the specs for the computer: 
AMD Athlon(tm) 64 Processor
3200+
2.20 GHz 2.00 gb of RAM

It currently has 5.32 gb of space free.

I originally wanted to install a lighter weight version of Linux since this hardware is older, but I've had no luck getting those installed either.

When I turn the computer on, I have the option of booting in either Ubuntu or XP. I can get Ubuntu to load if I opt to use 'demo mode.' And from there, I've tried using the option to install it.

---

### Post by Greenwick on 2014-12-13
I've uninstalled Virtual Clone Drive, and am giving Unetbootin a shot, to create the live USB.

---

### Post by grahammechanical on 2014-12-13
> [COLOR=#000000]When I turn the computer on, I have the option of booting in either Ubuntu or XP. [/COLOR]

I am still confused. That statement sounds like you are seeing the Grub boot menu which would indicate the Ubuntu has been installed. What happens when you select each of the options? Does XP load? Does Ubuntu load? Or does the loading get a certain distance but no further. If Ubuntu is only partially loading we need to know what you see on the screen in order to try and work out at what point the loading stops. That will help work out what is wrong.

It also helps if we know what version of Ubuntu you are working with. If Ubuntu is installed but not loading it could be that the proprietary video driver no longer supports that video card. Ubuntu will install the latest video drivers. The manufacturers often drop support for old graphic cards.

If Ubuntu is installed and you are seeing the Grub boot menu, then you could try loading Recovery Mode and then at the Recovery menu selecting Resume. If you get to a desktop you can then use Additional Drivers to change video drivers. You might have to use the open source driver.

I cannot give detailed directions without knowing the version of Ubuntu.

Regards.

---

### Post by Greenwick on 2014-12-14
I was trying to install the latest version of Ubuntu, but had a previous version of Ubuntu on the system. I'm not sure what version it was. It would stop loading if I chose Ubuntu from the menu, but would pull up the demo version of Ubuntu.  I tried doing this with Lubuntu on a USB stick; it erased both Windows and the previously downloaded version of Ubuntu, but then wouldn't finish the install. Instead of saying an iso file was mounted, it said there was something wrong with my install device.

I managed to get into the Lubuntu demo and then download Lubuntu from there. I have to pull up the BIOS menu in order for it to work, but once I do that, it works fine. So I'm going to assume something was horribly wrong with my previous install, Virtual Clone Drive was interfering with the install, something was wrong with my USB stick, and probably there is something funky in my hardware.

---

