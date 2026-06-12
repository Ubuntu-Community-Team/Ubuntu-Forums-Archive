---
title: "How small can my ubuntu partition be?"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by Johnsie on 2007-02-11
Hi, I have very limited space on my hard disk. I want to install Ubuntu but really need to be stingy with disk space. What is the minum partition size that a standard ubuntu install can be done on? Also, if I decide I dont wanna keep ubuntu on the disk, can I give the space back to the ntfs file system?

---

### Post by RandomJoe on 2007-02-11
I just checked a fresh Edgy install with no extras yet, and it is taking up around 2.4GB.  You will need more space than that, of course, to do much with it.  10GB would be a safe number, although you could pare down closer and just see what happens...  Worst case, it's just going to die while installing files because it runs out of space.

You will also probably want/need a swap partition, the rule of thumb is 2x memory size although I usually just do same amount as memory unless it's a really low-mem machine.  (Swap's so slow, I'd rather just go without.)

AFAIK, there's no way to merge unused space into an existing NTFS partition, but then I haven't run Windows on my own systems in a very long time...

---

### Post by aysiu on 2007-02-11
If you're willing to do a barebones install with X, IceWM, and a handful of productivity applications (web browser, office suite, email client) and no other frills, you could probably make the partition 1.5 GB.

---

### Post by eapache on 2007-02-11
I don't know how much space ubuntu takes, but I know that if you don't want to keep it, use the gparted livecd here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

which can erase the ubuntu partition and then grow the ntfs to fill the empty space.

---

