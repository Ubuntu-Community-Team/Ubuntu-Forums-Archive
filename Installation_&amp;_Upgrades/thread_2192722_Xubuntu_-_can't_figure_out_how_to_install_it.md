---
title: "Xubuntu - can't figure out how to install it"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by scratch65535 on 2013-12-09
This is my first experience with linux but not with unicies - I go back to the beginnings with FreeBSD, and before that SysV and SCO, Ultrix, etc.

I'm trying to install Xubuntu 13.10 64bit from the live cd (dvd really since it's oversize). 

I first tried the regular-flavor ubuntu v12.04.3.  Since it scared me by not bothering to ask which disk I wanted it to install to, I disabled all the disks but the target one for the Xubuntu install.  It's a data disc with 2 partitions, one unformatted and intended for the installation and the other dedicated to NTFS.

I chose "install" rather than "try" when Xubuntu booted, but it doesn't seem to know how to install itself, and it's *very* sparing with instructions on how I should fix whatever it thinks is wrong.

Can someone point me to a detailed walk-through, or offer advice?  Thanks.

---

### Post by howefield on 2013-12-09
An idea of where in the installation process that you are stuck might be useful. Help others to help you.

---

### Post by scratch65535 on 2013-12-09
Thanks for the response.

I'm past that particular problem (the installer lacks a tip-off to let folk know they should dclick the partition's name to access the formatter et al) and garden-paths anyone who's familiar with bsd by not reminding them that they must allocate swap by hand, making the operation a go-back-and-do-it-again process), but at the end the installer crashed because it couldn't install grub into '/target/'.  I'm guessing '/target/' may be undefined in the installer.  Anyway, it crashed and hung the system, so now I'm waiting for a copy of 12.04.3 to finish downloading.  I'll try it and see whether it works better.

---

