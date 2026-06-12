---
title: "problems with installing Ubuntu"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by 2pacalypse on 2006-06-07
I recently ran the update from Breezy Badger to Dapper Drake, but unfortunatly, in the middle of the installation Ubuntu decided to kick me out into the user login screen, and thus the upgrade was stopped in the middle. when i tried to run the updater again, Ubuntu freezed completely and didnt responded to anything for half an hour, then I got tired of waiting and did a reboot but now, i cant boot up my system at all! he constantly giving me somekinda "GRUB error" message and i cant boot up, when i tried to run the Breezy Badger installer to reinstall my Ubuntu he installed the software but i still had this cursed GRUB error, then i tried to download the Dapper Drake Install cd, but he crashed in the middle of the install several times and only in the 13th or 14th attempt he agreed to install. only to give me the GRUB error message again. only after i fully formatted my entire computer (and thus losing around 2Gigs of unbacked up data) the grub error disappered(only to magicly reapear a day later), only to be replaced by some Kernel panic message. now none of my systems agree's to work, niether SuSE,Ubuntu Badger and Drake or Mandrake agrees to be installed, most of the time he simply crashes during the install but on times i do succeed in installing, he spits me the Kernel panic or GRUB error messages. what should i do? this grub has simply destroyed all my system.. the only thing that works in the damn bios

---

### Post by lkagan on 2006-06-07
This sounds like a hardware problem, namely memory.  If you have the CD, can you run the OS from the CD for a while without any problems?  I suspect that you will have problems.  You might want to try using some other memory.

Larry

---

### Post by cilynx on 2006-06-07
I would second that.  Another option is a dying hard drive.  You could have stumbled upon it during the heavy read/write of the update process.

---

### Post by rcarring on 2006-06-07
Try running the Live CD for a couple of hours, using applications as you would if you were running an installed to hard disk system.

It is possible that memory is an issue, alternatively if the hard disk is on its way out, a lowlevel format may bring it back for a limited period of time.

---

### Post by 2pacalypse on 2006-06-07
the live-cd OS works fine.my harddrive works fine, im pretty much sure that the prob isnt in it, he worked exellent just a few days ago. further more, this problem is happening on two diffrent harddrives. its impossible that both have the same problem in the same time. and about the format, i already did full formats. on the entire computer for 3 times, and now im gonna try again. i ran memtest on my machine to look for errors but no errors were found so I presume that my RAM is ok too.

heres a screenshot of the problem
[img]http://img257.imageshack.us/img257/2596/img00840zt.jpg[/img]

any1 has an idea on how to fix this damn Kernel panic? does it have to do with that ram thingie? doesnt my run cut it? (i got 512)

---

### Post by cilynx on 2006-06-07
That says pretty cut and dry that it can't find the first partition on your first hard drive.  That's what block(0,0) means.  Are you using SATA or anything odd like that?

EDIT:
Also, I just noticed that your kernel is on hdb1.  Why is it looking for your filesystem on hda?

Continuing on, "ran out of compressed data" tells me that something messed up when writing the initramfs to the disk during the install.

---

