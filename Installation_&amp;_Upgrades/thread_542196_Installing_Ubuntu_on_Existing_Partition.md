---
title: "Installing Ubuntu on Existing Partition"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by Latoneyde on 2007-09-03
I have a problem. I have an existing 50 gig EMPTY partition that i want to stall ubuntu on... But i can't seem to get ubuntu to install on that partition, i'm getting an error saying something about "/" root extention not valid or something of that sort. What do i need to do to get ubuntu to recognise this partition? Do i need to reformat it?

---

### Post by merlinus on 2007-09-03
Ubuntu will not recognize unallocated space, so it will need to be formatted first.

Then you will need to specify the mountpoint, / (root).  You can do this by right-clicking on the partition and selecting from a dropdown list.

You will also need about 1.5G for a /swap partition, and you also may wish to allocate part of your free space for /home.

-merlin

---

### Post by Latoneyde on 2007-09-03
It is already formatted (NTFS)....Should I format it in a different format?


And for that /swap partition, is that created in the ubuntu installation?

---

### Post by merlinus on 2007-09-03
You might format it as ext3.

gparted live cd can do this for you beforehand:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

/swap will be created during installation.

-merlin

---

