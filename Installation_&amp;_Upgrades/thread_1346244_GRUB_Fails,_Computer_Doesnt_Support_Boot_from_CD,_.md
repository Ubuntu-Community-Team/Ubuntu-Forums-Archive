---
title: "GRUB Fails, Computer Doesnt Support Boot from CD, USB"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by blitzracer on 2009-12-04
I have a bit of a predicament mostly because of my own Adventurous stupidity :P
Today I was installing a partition of Damn Small Linux on a older Toshiba laptop of mine, the bios in the thing doesn't support changing the boot priority to a cd, and the DSL CD and the Ubuntu CD are my only course of rescue int his case. To get around this, the only fix is to unplug the hard drive so it will carry on its standard boot priority through the next steps. til it hits the CD and boots from it. I tried the textbook grub procedure

Sudo grub
find /boot/grub/stage1
etc...

but it cannot find grub stage1, it is because the computer itself wont remount the harddrive after it being unplugged, turned on and plugged back in. It is an old laptop and wont support usb booting and im thinking the only way to fix this is use a GRUB CD and try to write a new Master boot record. but I run into the problem that I still have to boot off a cd rendering my HD invisible to all programs. The only other way (and how I used to boot the live cd) was install a option in GRUB to boot to the CD, that prevents unplugging the hard drive and keeps this from occurring. If anyone has and Idea (however crazy) let me know Id hate to throw out a perfectly good computer :(

Computer Info

Toshiba Satelite A-15
30gb HD
BIOS supports:
 HDD, FDD, CD, LAN
in that order but priority is 
unchangeable and the HDD 
inevitably boots first (nice going Toshiba)
230megs of ram
Intel graphics card
ACPI BIOS Version 1.30 (searched Toshiba's site for update.. this is the latest)
sad thing is this machines bios has never been upgraded to my knowledge

---

### Post by u.b.u.n.t.u on 2009-12-04
Is networking, and writing to the HDD that way feasible?

---

### Post by blitzracer on 2009-12-05
Unfortunately because of the boot order the bios takes; networking is the last thing on the list for it to boot from  

I almost think I need to find a bios modification to put cd's before the hard drive. or find a way to force boot the cd like WUBI did in windows. id need a custom live CD for that which include WINE but its the most of a workaround I can come up with. Oh yeah heres another kick, there's not an Ethernet chord in this appartment why? I have no clue, and getting my network card to work on a non-persistant boot of DSL? wow.... 

so the 3 ideas are from me are:

Persistent force boot to CD script from somewhere (i'm not a programmer) which I can run in live cd of either DSL or Ubuntu 

A BIOS Modification with a changed boot order (dangerous...) 

Network install. (no hard line connection)

but something else just occurred to me,
if I could just get the computer to recognize and mount the hard drive so that Linux can see it, that would help a lot.

---

### Post by u.b.u.n.t.u on 2009-12-05
Removing the HDD, installing Ubuntu, then replacing the HDD?

Working with such dated technology may have a tinkering value but that is about it.

I can't suggest anything more.

Have fun! lol

---

