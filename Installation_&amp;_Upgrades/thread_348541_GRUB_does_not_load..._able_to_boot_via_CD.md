---
title: "GRUB does not load... able to boot via CD"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by do-U-boon-2 on 2007-01-28
I wiped some partitions with an older version of FC that I rarely booted, installed 6.10, 
but booting ain't happening.  I just get 'GRUB ' and that's all.  If I boot from the CD, 
and select the last option to boot from the first hard drive, I then get the full GRUB 
menu and can boot either Ubuntu or XP.  Any ideas?

BTW, if I boot Ubuntu, then sudo grub and type 'find /boot/grub/stage1' I get an error:

Error 15: File not found

...although it is clearly there!

A grub-install /dev/hda did not fix the problem either...

TIA!!!

---

### Post by housam on 2007-01-29
Try to use the [super grub disk ]("http://supergrub.forjamari.linex.org/")it may help fix it.

---

### Post by dannyboy79 on 2007-01-29
i have tried that, I did both the restrore grub to mbr automatically as well as manually and still nothing??? I can use the sgd to boot the mbr and ubuntu starts but the bios just won't boot it??? it won't even start grub, the bios comes to an end where grub normally starts but nothing happens? and yes, i have made sure that the bios has the correct hdd being booted first.

---

### Post by do-U-boon-2 on 2007-01-29
Hmm, just for grins, I blew away 6.10 and installed FC6 in its place.  GRUB works 
just fine now.   :-0

Seems like this should be something the installer should *always* get right.  Perhaps 
I'll just wait for a better release.  It seems like a lot of people have trouble with the 
GRUB configuration.  Some of this is no doubt self-inflicted pain, but some of it seems 
to be the result of some weakness in the Ubuntu installation process.   :-(

---

