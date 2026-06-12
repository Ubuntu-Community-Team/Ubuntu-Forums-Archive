---
title: "need help with 10.10 netbook edition"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by FiveStarSky on 2010-10-13
Hey everyone, I'm new to all this so go slow.

I tried to install the netbook edition, and it said it installed fine, and when i reboot to run off the hard drive, it gives me a black screen with white text ( looks like a comand prompt )
says

Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.635-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

i've tried all of these, and nothing will let it boot up, unless i boot off the usb back into the trial/install thing, and when i boot up off the usb, i cant see my harddrive

(using an acer netbook, only 1 harddrive, no cd drive)

---

### Post by FiveStarSky on 2010-10-13
any help would be apreciated, i tryied to install windows again, but it cant find the hard drive, and i cant find the hard drive in the linux partition manager, only the usb drive.

---

### Post by cariboo on 2010-10-13
What happens when you select one of the menu entries in grub? Does it start to boot, then seem to lock up? does it take you to a command prompt?

More info would be helpful.

---

### Post by FiveStarSky on 2010-10-13
boot up, select the Ubuntu, with Linux 2.6.35-22-generic, it waits a second then says.

Gave up waiting for the root device. Common problems:
- boot args (cat/proc/cmdline)
 - check rootdelay= (did the system wait long enough)
 - check root= (did the system wait for the right device?)
- Missing Modules (cat/proc/modules; ls/dec)
ALERT! /dev/disk/by-uuid/29466446-ca20-45be-a1ce-59553cfcf9ba does not exist.
Dropping to a shell!

BusyBox v1.15.3 (ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)



The only think i can think of at the moment is take it to a shop where they would charge god knows what to fix it, basically, i can boot linux up off a 4gig flash drive, other than that, i cant do sh*t, (cant even re-install windows cuz it cant find the hard drive)

---

### Post by FiveStarSky on 2010-10-13
anyone? or can at least anyone tell me how i can at least put windows back on it?

---

### Post by davideagle on 2010-10-17
Having the same problem here.

Will try to find a solution to this, seems at first glance that it is not trying to mount the right disk.

---

