---
title: "dual boot ubuntu and winme"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by aparolin on 2010-12-31
greetings,
starting the new year with ubuntu 10.10 :)
 
i have acquired a used HP pentiumD 820, with asus p5lp-le motherboard, 2gb sdram, cd drive, no floppy.
 
i would like to dual-boot the system with ubuntu 10.10 and winme.
(hold the growns)
 
i have copies of 10.10 iso and win disks and i bought a brand new 700mb sata hdd.
 
i assume that i should format the hdd first. 
any special differences between formatting of sata vs ide hdd?
should i format before installation?
 
i would like the system to automatically boot to ubuntu for normal everyday use, but occassionally manually to boot to winme. 
 
sure would appreciate the responses;
thx
and happy new year!!!

---

### Post by tommcd on 2011-01-01
> **aparolin said:**
> 
i have copies of 10.10 iso and win disks and i bought a brand new 700mb sata hdd.
Is 700 *Megabytes* a typo??? I assume you mean 700 *Gigabytes* or something similar??? 
> **aparolin said:**
> 
i assume that i should format the hdd first. 
any special differences between formatting of sata vs ide hdd?
should i format before installation?
Install Windows first to whatever size partition you want. Leave the rest of the drive unallocated.
Then install Ubuntu to the rest of the hard drive. 
For the most ideal install, you should create 3 partitions for Ubuntu: root, swap, and home. This will keep all your data and settings on a separate home partition which will make reinstalling Ubuntu much easier. You will need to choose manual partitioning during the Ubuntu install to do this. See this:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
> **aparolin said:**
> 
i would like the system to automatically boot to ubuntu for normal everyday use, but occassionally manually to boot to winme. 

This is what you will get when you install ubuntu.
Here are 2 great sites to help you get started:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And for dual booting:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by aparolin on 2011-01-02
thx;

appreciate the info;

when creating a dual boot syst; i guess/or it seems that i will have to choose one or the other at each time i startup the computer?

am i in error???

again thx:)

---

### Post by tommcd on 2011-01-03
> **aparolin said:**
> 
when creating a dual boot syst; i guess/or it seems that i will have to choose one or the other at each time i startup the computer?

Yes this is true. The grub2 menu will show on the screen when you boot the computer and give you the option of booting Ubuntu (which will be the default) or Windows.

---

