---
title: "floppy install? sbm won't work"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by tesla_coil on 2005-07-15
hi

i am trying to install on a sony vaio laptop pcg-505ve...need to use floppy to boot, and i can't find a floppy img for ubuntu online

before you write back suggesting smart boot manager or net install, know that i have tried - these don't work.  i have only external devices - usb or pcmcia cdrom, external floppy, pcmcia network card.

one suggestion i read was to do a minimal install with debian disks, then change the sources to hoary and apt-update the packages.  this doesn't work for me either.

is there an ubuntu floppy img i can use to begin this install?

thx

---

### Post by mr_mop on 2005-07-15
There is no ubuntu floppy install as such.  It is possible, but its quite fiddly.
I just installed ubuntu on a Toshiba with floppies and it works fine.

OK this link is this:
[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

I had to do it slightly differently as I didn't have a windows install ( no CDROM drive, so how could I :)
Anyway I did have DOS 6 on floppies, so I installed that to a small 200MB partition at the start of the HD.  Then I installed GRUB for DOS, following the readme in the GRUB zip file.
Once I'd done that I copied across the menu.lst file the poster had attached to his post, and that allowed me to boot the linux kernel in the DOS partition.
I could then install the base system, and then the full system.

I hope this helps :)

EDIT:

Oh and about the floppy disc option.  You can use the debian floppy to install the base system, and then change the sources file to look at the ubuntu mirror.  However I didn't like this as it doesn't set up sudo correctly and its not a _proper_ ubuntu install IMO.

MM

---

