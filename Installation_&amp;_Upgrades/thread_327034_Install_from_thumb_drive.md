---
title: "Install from thumb drive?"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by scudellari on 2006-12-28
Hi all,
A friend of mine has this really beat up laptop on which he wants to install Ubutunu.  But neither its CD drive nor onboard ethernet card work at the moment.  The only way I could think of installing Linux is by booting off a thumb drive and installing from there... but I have only heard of people installing Linux ONTO a thumb drive, not FROM a thumb drive.

Is this possible?  Is it possible to "burn" the Ubuntu iso onto the thumb (1GB)?  I assume simply copying all the files from the ISO onto the drive will not make it bootable/probably wouldn't work for other reasons of which I am not aware.

Anyway, some semi-detailed instructions on how to go about this would be helpful.

FYI:  He has a PCMCIA card that he uses to connect to the net, but I assume there would be no way to do a network install between having to load drivers(?) for the card and the CD drive not working.

Thanks,
Ryan

---

### Post by SoggyCornflake on 2006-12-28
> **scudellari said:**
> Hi all,
Is this possible?  Is it possible to "burn" the Ubuntu iso onto the thumb (1GB)?  I assume simply copying all the files from the ISO onto the drive will not make it bootable/probably wouldn't work for other reasons of which I am not aware.


Anyway, some semi-detailed instructions on how to go about this would be helpful.
. . .  Thanks,
Ryan

I don't know if this approach would be the best route, but I think it should work.

You might be able to load[ **DSL **linux]("http://www.damnsmalllinux.org/") onto a thumb drive from another computer.  Then move that to the laptop in question. 

First burn **DSL **onto a CD-ROM.  To load it onto a thumb drive boot off the **DSL **CDROM with the USB thumb drive inserted on the source computer.  Then follow the menu commands to save DSL to a thumb drive.

Assuming you can boot off the USB port (This is more possible with more recent laptops) 
DSL should be able to boot up off the Thumb drive.  (there's a good chance that a lot of devices won't work with **DSL **since laptops tend to be less standard than PCs)

Once **DSL **boots up, follow the menu commands to save to the laptop's hard drive.

 **DSL **is **Knoppix **based, so once loaded onto the laptop, you can add the Ubuntu sources and migrate to **Ubuntu**.

---

### Post by bernied on 2006-12-28
Can you get the PCMCIA card working with another live-cd linux? Like slax? Slax is designed to be installed onto USB stick and has lots of addable modules, they might be able to get the card working, then you could do a net-install. I suspect this might be quicker than trying to get the ubuntu live-cd to run from a stick.

If I was trying to get the live-cd to run from the stick I'd do something like
- mount the cd (or mount the .iso image if you want to save a cd)
- copy all the files from the cd to the stick
- have a look around the / directory for things that look like they should boot, I think this is in the isolinux folder - the treasure is in /isolinux/isolinux.cfg
- work out what boot parameters you need (root location, name/location of kernel, name/location of initrd, any kernel boot parameters - like ramdisks) don't include the quiet option, it conceals useful information
- install grub on the usb stick and translate the stuff in isolinux.cfg into a menu.lst file
- boot it and see what goes wrong.

---

