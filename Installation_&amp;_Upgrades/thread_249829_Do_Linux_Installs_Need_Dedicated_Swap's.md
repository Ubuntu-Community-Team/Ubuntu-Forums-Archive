---
title: "Do Linux Installs Need Dedicated Swap's"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by JWells on 2006-09-03
If I'm going to install two different Linux distributions (Xandros and Ubuntu) on one hard disk, do they need seperate swap partitions, or can they share the same swap partition?  And just how big should the swap partition be (I have 1GB of RAM)?  Right now, I have a 10GB partition for Xandros, followed by a 1.5GB swap partition, then a 10GB partition for Ubuntu, followed by a 1.5GB swap partition.  Is this unnecessary?  Are the OS's able to find the swap partition if its not adjacent?  Do I need to do anything special for both OS's to share the same swap partition?  Thanks for answering what is probably a dumb question.

---

### Post by Lord Illidan on 2006-09-03
It's not a dumb question.

Both OSES can share the same swap partition. I have DreamLinux, Zenwalk and Ubuntu all sharing the same swap on my machine.

1.5 gb should be enough.

As for configuring them to use the same swap partition, during installation make sure that they use the same partition for swap. In Ubuntu's install it is quite easy.. just make sure it uses the right /dev/hdc or whatever.

---

### Post by JWells on 2006-09-03
Seems reasonable.  On any particular install, how do you determine whether or not the OS is even aware of the swap file?  How do you test this?

---

### Post by Sef on 2006-09-03
In general, swap should be double the ram.  However, once you get past 1 gb ram, swap really isn't needed, unless u do heavy gaming or video editing.

---

