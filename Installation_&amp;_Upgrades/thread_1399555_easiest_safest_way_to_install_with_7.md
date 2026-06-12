---
title: "easiest/ safest way to install with 7"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by GuitarG20 on 2010-02-05
So what is the easiest way to install Ubuntu with win7 also on the computer?
I'm asking because last time I ran Ubuntu it was Wubi'd into XP and then it broke, breaking XP's bootkernel and then keeping me from booting into anything...

---

### Post by wilee-nilee on 2010-02-05
You need a free partition space for the Ubuntu install. You should use the W7 disk management to resize the W7 partitions, if you right click the partition in the disk management program you can shrink the partition or expand if there is space. This is just a start so ask more questions.

---

### Post by GuitarG20 on 2010-02-05
okay, so what's the problem with wubi and other programs like that then? seems like they'd make their own partition...

---

### Post by gspat on 2010-02-05
use disk manager to resize the HDD to make room for the partitions you want to make

create at least a partition for the swap and 1 partition for ubuntu itself (/), with preferably one more for your /home as well

start up the computer with the livecd and choose try without any changes

click the install icon on the desktop once the livecd boots

use the manual partition option and select the partitions to use that you created in win7

done.

---

### Post by sailthesea on 2010-02-05
> **GuitarG20 said:**
> okay, so what's the problem with wubi and other programs like that then? seems like they'd make their own partition...

Wubi doesn't work like that 
It creates a virtual disc in the windows partition and runs within it I have used it to great effect in the past but there seem to be issues with 9.10,Wubi and W7 in general so I'd give it a miss for now
 Make a nice partition for ubuntu and dual boot Fixing any Grub problem should only take a minute It's pretty well documented now

---

### Post by wilee-nilee on 2010-02-05
You can also install to a thumb the ISO and leave a persistent space all toyaling 4 gigs with the Ubuntu usb creator. You can also do a full install to a thumb a 8 gig would work at best for a minimum size. The full install is done with a live CD and pointing the install and grub at the tgumb in the install gui's. These methods allow you to have Ubuntu without modifying your computer, and are bootable on other computers.

---

