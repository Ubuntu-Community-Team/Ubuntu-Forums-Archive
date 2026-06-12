---
title: "Ubuntu Install Stops After Loading Linux Kernel"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Armando Penblade on 2008-08-10
I am running a brand new desktop, ASUS P5Q PRO mobo, Intel Q9300 processor, 4GB G-Skill 800mhz DDR2 RAM, Western Digital 640GB HD (With a 50GB unformatted partition ready for Linux), ATI 4870HD PCI Express graphics card, Creative Labs X-Fi Xtreme-Gamer 7.1 PCI soundcard, and am completely unable to get the install going.

I've got 0 experience using Linux, to be completely fair. . . I've done a couple of things on school Unix systems to register accounts with the CS department and such, b ut I really have no idea what i'm doing here.

Essentially, the kernel loads to 100% when I tell it to install or boot from the CD, then it hangs.  75% of the time, it spins the CD and HD for a few minutes, then gives me a black screen with a blinking cursor in the top corner, then stops there.  25% of the time, it reboots itself entirely and reloads from the CD.

I've got no idea what to try, or how to implement even the most basic of suggestions, so detailed instructions would be enormously appreciated--I've been using computers daily since 1996, so you don't need to necessarily talk down to me, but it's been awhile since I wrangled a command line to do more than dir /w, and I've got no idea how to access a command line from the linux installer, since I can't even get it to fully load.

---

### Post by Armando Penblade on 2008-08-10
So, an update.

Setting "noacpi" into the command line had zero effect, as did the "Safe Graphics" mode. . . removing Quick Splash did not show me any extra error messages, just the same old, same old.  Kernel loads to 100%, the system stops, then gives me a blinking cursor.

I can't verify the integrity of my disc, because it tries to load the Linux kernel to do that, and when it does, it hangs in the very same place!!!  The CD loads fine in windows, it seems, and the CD drive in question installed Windows and a bevy of drivers and programs without a hitch.  My ISO looks dandy, and I've never had bad burning problems before.

Just trying to answer the typical suggestions.  Is this a hardware thing?  Is it just impossible ofr Linux to run? Or am I missing something obvious?

---

### Post by Armando Penblade on 2008-08-10
*bump*

Which I'll continue to do till someone can help me figure this out :)

---

### Post by ctal on 2008-08-10
I just had the same problem trying to install 8.04.1 on a five-year old Asus P4C800 Deluxe.  I resolved it by disconnecting an external usb flash card reader.  Legacy USB support had been enabled in the bios; I suspect the problem would not have occurred if legacy usb support were disabled, but then the installer would not have been able to see my usb keyboard.  

Hope that helps.
-- Al

---

### Post by Armando Penblade on 2008-08-11
Just tried the USB solution, no good--removed all USB devices, turned off legacy support, and even added the saffe graphics/noacpi codes when the USB stuff didn't work.  in other words, doesn't look like a USB problem.

any other suggestions? :(

---

### Post by Armando Penblade on 2008-08-11
still searching for solutions. . .

---

### Post by ctal on 2008-08-11
I'd guess that it is getting mixed up as to drive numbering, which is what apparently caused the problem when I had my flash card reader installed.  If you have anything that could be considered a drive (flash card reader, optical drive, etc.) other than the WD640 onto which you want to install, I'd suggest disconnecting it temporarily.  And connect the WD640 to the lowest numbered sata connector on the mobo, sata0 or similar.

---

