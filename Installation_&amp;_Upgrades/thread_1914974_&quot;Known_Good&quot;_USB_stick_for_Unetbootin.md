---
title: "&quot;Known Good&quot; USB stick for Unetbootin?"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2012-01-25
Tried creating a bootable Linux installer yesterday.  Using a GParted LiveCD, I formatted a thumb drive to fat32 as suggested at Unetbootin website.  Downloaded unetbootin from repos.  Fired up the application and asked it to create a bootable drive from an .iso saved to the Desktop.  Everything appeared to go OK but the stick won't boot.    

I tried the drive in a couple of different PC's.  Using the Boot Options keys, I chose USB device.  In both cases, the PC appears to look at the thumb drive, then boots from HDD.

If I open the thumb drive from a running Linux PC, the contents look like a LiveCD to me; the same filenames, etc.

I think I'll try again by booting from a LiveCD, then going to Start-Up Disc Creator.  If that doesn't work I'll try again using PenDrive on a Windows PC.  In the meantime can anyone suggest a "known good" brand of thumb drive?  Some comments online indicate some thumb drives just don't work as bootable.

---

### Post by jerrrys on 2012-01-25
Some usb's have installed security software and can give you trouble.

Myself, I use PNY usb's for linux without trouble.  They have been totally dependable and best part; PNY is cheap.

I really think just about any usb will work that comes with nothing pre-installed on it.

---

### Post by Bartender on 2012-01-25
Yeah, I know what you mean.  I'm careful to buy plain old blank drives.  I've got a 2GB PNY, will try that next.

I got nowheres with PenDrive.  I tried several CD's but couldn't get any of them to load into PenDrive.  It looked like I coulda downloaded but I'm on satellite.  Can't waste bandwidth.

So I tried Ubuntu Start-Up Disk Creator.  I'm getting this same message (attached) whether I try from a LiveCD or try from the Desktop.

EDIT: Well, I got further with the PNY thumb drive than the first one.  The first drive is brand-named Tone.  A guy gave it to me.

Using the PNY, Ubuntu Start-Up Disk Creator gave me no troubles.  Did its thing.  But when I rebooted trying to use the disc I got a black screen.  

"No init found.  Try passing init: bootary"
"BusyBox v.1.33"

There was some other stuff, but when we get to this sort of thing I retreat.

ANOTHER EDIT: Sorry, it's a Sony-branded thumb drive I was trying out next, not PNY. So I tried it again, but this time I asked the Ubuntu Start-up Disk Creator (USUDC) to "Erase Disk" first.  Then did the rest of it over again.  This time it's working.

---

### Post by Mark Phelps on 2012-01-26
It may not be the USB stick -- it may be unetbootin.

I tried using unetbooting to create a bootable USB for 12.04 -- and while the app said it worked, the USB stick would not boot.

So, I tried again, using the same USB stick, but this time, with the Universal USB Installer, downloaded from PendriveLinux.com.

This time, using the same USB stick, it booted just fine.

---

