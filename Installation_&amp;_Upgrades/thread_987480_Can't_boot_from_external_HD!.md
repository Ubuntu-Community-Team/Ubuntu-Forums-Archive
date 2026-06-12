---
title: "Can't boot from external HD!"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by snakeman21 on 2008-11-19
So here's what I did:  My wife's computer has windows XP on it, and she won't let me install ubuntu for a dual boot.  So I got a 230gb external usb hard drive to use instead.  I pulled out her hard drive, to avoid accidentally formatting it, and used a live CD of Ubuntu 8.10 to install it to the external HD.  The HD was formatted to FAT32.  The installation went smoothly, everything seemed to work, and when I rebooted, it worked perfectly.  So I shut down the computer, and put my wife's HD back in the laptop.  But now I've realized that I can't boot from the external drive unless I pull the main HD!  Shaina doesn't want me opening her computer every time I want to run linux, so what can I do?  I've set it up in the BIOS, but even when I hit F11 for the boot menu, the usb HD isn't on the list of options, as if the computer doesn't even know it's there.  I can view it in windows, but I simply cannot make it boot from it without pulling her main HD first.

---

### Post by Linteg on 2008-11-19
Well, is there no setting in your bios for boot device priority? If you prioritize any USB drives above HDDs I would believe it would work. If it does, I'd recommend that you either set up grub (Ubuntu's boot loader) to be able to boot XP or that you do the opposite, let Window's boot loader (ntloader) boot ubuntu. See page 5 and 6 of [this guide](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm).

---

### Post by snakeman21 on 2008-11-19
Yes, there IS a section in the bios, but like I said before, even though I set the priority to the usb drive, the computer will not acknowledge that there IS a usb hd... Unless the main hd is disconnected.
 
But I have been trying it more in the meantime, and now it's worked a couple of times.  It's very random, very sporadic.  Most of the time, it will not detect the usb hd, but every four or five restarts, it will.  I am not changing the bios in between restarts, so it's very confusing.  It seems like it boots from the external drive whenever it feel like it, but most of the time will not.

---

### Post by snakeman21 on 2008-11-19
Ha ha... wow... I feel really stupid.  It was a bad USB connection!  The cable wasn't plugged all the way into the external drive!  Thanks for the help, anyways!  Sorry! ](*,)

---

