---
title: "Pentium M 1.2 GHz, 640 MB ram: Neither version of 12.04 installs"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2013-12-21
I am trying to upgrade from 11.04 by doing a fresh install of 12.04 on this older Dell laptop.

But I can get neither of the offered 12.04 versions to install.

ubuntu-12.04.3-desktop-i386.iso
ubuntu-12.04.3-desktop-amd64.iso

Both get an error "this kernel requires an x86-64CPU. But only detected an i686 CPU"

what can I do?

---

### Post by Bucky Ball on 2013-12-21
Stick with the i386 and forget the amd64. Sounds like you have a single core processor. 

More information would help, for instance the specs of this older laptop, when you receive this error message and what happens after it, and anything you have tried so far to remedy this.

For starters, though, try the i386 alternate ISO. The same but text based so no disco bells and whistles. This can succeed where the desktop version fails. Same end result.

---

### Post by pjstock on 2013-12-21
the i386 iso is not working.


Processor / Chipset
    CPU Intel Pentium M 1.2 GHz
    Cache L2 cache - 1.0 MB
    Power Efficiency Low-Voltage (LV)
    Front Side Bus 400.0 MHz
    Chipset Intel 855PM

Memory

    RAM 640.0 MB
    Max RAM Supported 1.125 GB
    Technology DDR SDRAM
    Speed 266.0 MHz / PC2100
    Slots Qty 1
    Empty Slots 0.0

---

### Post by fantab on 2013-12-21
With only 640Mb of RAM you cannot install regular Ubuntu, as it needs more RAM to work with amongst other requirements.
Your best bet is [Lubuntu Minimal Install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). 
If your systems support more RAM then, if possible, add more RAM.

Good Luck...

---

### Post by Bucky Ball on 2013-12-21
Or just a minimal install and add any one of the lightweight desktop environments, lxde or xfce or any of the many others. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by mörgæs on 2013-12-21
Yes, Lubuntu Minimal is a good option.
Here's a solution if you encounter [PAE]("https://help.ubuntu.com/community/PAE") problems.

---

### Post by pjstock on 2013-12-22
Indeed, I hit the PAE problem when trying to install Lubuntu.

tell me though, I have a reasonably functional version of Ubuntu 11.04 running on this unit. Why should I continue fiddling with upgrades or better versions? Why should one care if support has been ended?

---

### Post by mörgæs on 2013-12-22
Because there will be no security bug fixes (actually you have been vulnerable for more than a year). 

Why not give it a fresh install of Bodhi?

---

### Post by pjstock on 2013-12-29
just installed Bodhi now and am fiddling with it. But My Goodness, what a slick little setup this seems to be. And everything just ... works. wireless and all.
many thanks for your guidance and patience.
Peter

---

### Post by Bucky Ball on 2013-12-29
Yea, have been playing with Bodhi in virtual box and really quite like it, too.

Please mark thread as solved (if it is) to help others by following link in my signature. ;)

---

