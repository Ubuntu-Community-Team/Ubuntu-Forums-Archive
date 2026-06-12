---
title: "Vista (Internal HD) + 7.10 (4gb USB Flash) Problems"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by rickatnight11 on 2008-03-18
Well, my laptop only has a 60gb internal harddrive with Vista Ultimate currently installed.  I wanted to start playing with Ubuntu again, and figured my 4gb USB flash drive would be the perfect place to install it without messing with my internal harddrive.  I installed 7.10 Gutsy to the flash drive with no problem, restarted, booted it up, and got all the drivers working great.  I assumed that because i specified the flash drive ONLY and never saw any option to even touch the internal hard-drive that Ubuntu would leave it alone and install GRUB and itself on just the flash drive.  My intended result would be that my system would boot Vista just like it always has with the USB drive removed, but load the GRUB bootloader when the USB Flash drive was inserted.  No such luck.  Ubuntu went ahead and configured GRUB on my internal drive without saying anything about it, and now I can't boot Vista without the flash drive in the machine.  I get an error code 21 if not, which I supposed has to do with GRUB loading off of the harddrive and not being able to find Ubuntu.  I do have an image backup of the Vista drive before all of this so I can restore quite easily, but I would like to know how I can install Ubuntu to JUST the flash drive so that my laptop boots with the following situations:

[LIST=1]
[*]Boot with no USB device inserted - load Vista (no GRUB on my harddrive, system has no idea Ubuntu ever existed on it)
[*]Boot with USB device inserted - load GRUB from the flash drive and prompt normally for Ubuntu, Recovery mode, etc
[/LIST]

Thanks in advance!

---

### Post by rickatnight11 on 2008-03-18
Would physically removing the internal Hard Drive before booting the LiveCD and installing to the USB Flash Drive work?  That way only the USB Drive is able to be written to.

---

