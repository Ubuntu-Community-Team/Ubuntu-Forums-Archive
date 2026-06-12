---
title: "Make more space for Ubuntu with Gparted?"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by II Traveler II on 2011-07-26
This is a bit of a n00b question, but is there a way to adjust my partitions after installation? I'm dual booting with Windows 7, and I want to add another 75 GB to my Ubuntu 11.04 partition. But the Ubuntu partition is locked, and doesn't allow me to fill the unallocated space. Could anyone from the community help? Thanks!

---

### Post by coffeecat on 2011-07-26
You can't resize a partition that is mounted and especially you can't resize the root partition from inside the installation. You need to use Gparted from a live CD or live USB. One little gotcha. The live CD will automatically enable (and lock) any swap partition it finds. If your swap partition is a logical one, the extended partition will be locked as well, and if your Ubuntu root partition is also a logical one, this may limit what you can do. Simply right-click on the swap partition in Gparted and choose "swapoff".

Be forewarned that resizing a partition by 75GB can take a lo-o-ong time.

If you need any help, post a screenshot of the Gparted window from the live session.

---

### Post by II Traveler II on 2011-07-26
Thanks, coffeecat! That sounds like a bit of work haha. I still have over 70 GB of free space, so I probably won't bother. I was just wanting a little more for convenience. But again, thanks!

---

### Post by jerrrys on 2011-07-26
this may help

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

