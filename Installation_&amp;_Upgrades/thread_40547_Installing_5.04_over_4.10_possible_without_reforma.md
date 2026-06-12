---
title: "Installing 5.04 over 4.10 possible without reformatting?"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by akinwale on 2005-06-09
I'm almost through downloading the Hoary Hedgehog 5.04 release (over a 64k connection) ;). The thing is I have customised my 4.10 installation very much and it's going to be quite tasking and time consuming to have to recustomise a new installation.

Is it possible to install 5.04 and still preserve the existing configuration? And will it be worth it as compared to formatting the partition and reinstalling the whole package?

Thanks.

---

### Post by bored2k on 2005-06-09
[QUOTE=akinwale]I'm almost through downloading the Hoary Hedgehog 5.04 release (over a 64k connection) ;). The thing is I have customised my 4.10 installation very much and it's going to be quite tasking and time consuming to have to recustomise a new installation.

Is it possible to install 5.04 and still preserve the existing configuration? And will it be worth it as compared to formatting the partition and reinstalling the whole package?

Thanks.[/QUOTE]
 [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

You just need to dist-upgrade, not download the disc.

P.S. - Shinta Himura owns.

---

### Post by akinwale on 2005-06-09
Hmm... that's nice. Does it upgrade the kernel and replace XFree86 with X.org as well?

I still need the .ISO anyway as I intend to purchase a new hard disk (I'm running out of space on this old 6.4GB disk that I've been managing for a few months now. Not enough money to purchase a new one yet) :D

---

### Post by az on 2005-06-09
[QUOTE=akinwale]Hmm... that's nice. Does it upgrade the kernel and replace XFree86 with X.org as well?
[/QUOTE]


Yup.

---

### Post by Arthemys on 2005-06-09
Any of apt's functions keep me close to debian, and the .deb packaging setup. It's very fluid and easy if used properly.

---

### Post by juicemansam on 2005-06-09
I followed the above mentioned upgrade guide yesterday and pretty much ended up re-installing from scratch today. I'm not saying it won't work, either. One thing I did notice about the re-install (without formatting) was that the install would lock up at 33% during the grub install/setup and at 50% of the lilo install/setup (on different occations of course). One thing I did find was that the /etc/fstab was never written and was just the skeleton version (one commented line). The system did boot via manual floppy boot methods, but every time I was installing or configuring grub or lilo (or anything that needs them, such as a linux-image) I would get errors about drives not having BIOS equivalents. What saved me was that I happend to rename several directories to .old, such as /etc -> /etc.old, etc. That was my only way of restoring essential files such as fstab. Too bad I didn't save the /boot dir, I struggled a few hours attempting to install grub on the hard drive, and forget the menu.lst, it doesn't exist unless I manually make it.

---

