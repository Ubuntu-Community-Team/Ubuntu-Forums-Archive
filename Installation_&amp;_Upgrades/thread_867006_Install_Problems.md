---
title: "Install Problems"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by dr.marc.byrd on 2008-07-22
Here's my setup:
[LIST]
[*]ECS Elitegroup mobo GF7050VT-M
[*]Intel Core Duo 2.2 GHz
[*]2 GB RAM from "crucial" DDR2PC2-5300 unbuffered
[*]Seagate 500 GB 3.5" internal SATA 16 MB
[*]LG 20x internal super multi dvd rewriter, gh20 SATA
[/LIST]

Note:  no IDE, only SATA

Observations:
[LIST]
[*]Ubuntu 8 mem test fails at about 15%
[*]Without touching HD, ubuntu 8 runs fine (using it now)
[*]feisty fawn reports i/o errors early in install
[*]when attempting to install v.8 on hd w/ ext3, fails after about 5% with blinking cap-locks and other led (indicates kernel panic i believe)
[*]when attempting to install v8 on hd w/ reiserfs, gets much further, like 35%
[*]reseated everything
[*]have changed various bios settings, one at a time, no joy, resetting to defaults, no joy
[/LIST]

Theories:
[LIST=1]
[*]HD is the problem since I can write this post in hd-free mode, which uses both CD and mem (and network)
[*]mem is the problem since memtest fails (duh)
[*]some combination of hd and mem, perhaps dma?  (tried various nodma options... - no joy)
[/LIST]

Any help would be greatly appreciated.  I'm building this with my 10yo, hoping to give him some good early experiences, bragged about how helpful the forum will be ;^)

---

### Post by Pumalite on 2008-07-22
I would do a good mem test: 8 to 12 HRS.

---

### Post by prshah on 2008-07-22
> **dr.marc.byrd said:**
> 
[*]2 GB RAM from "crucial" DDR2PC2-5300 unbuffered
[LIST]
[*]Ubuntu 8 mem test fails at about 15%
[*]Without touching HD, ubuntu 8 runs fine (using it now)
[/LIST]



I'd say that you need to get the memory issue straightened out; all the other errors seem to me to be related symptoms.

Being able to successfully use the live CD is not a proper indicator; live CD usage requires very little RAM in use, possibly less than where your memory test reports errors. To confirm this: If you study the memtest output, it will show you where the errors start; then, load the live environment again, and keep loading programs until you come close to that memory level and see if you get flaky results (bad screen updates, patches, resets, unexpected behaviour, applications disappearing from the screen, application crash reports, etc).

memtest is a very reliable test, and has nothing to do with the hard disk drive.

If you'd still like further confirmation, disconnect the hard disk drive, or disable it in the BIOS, then run a memtest.

If memtest reports errors before the 1024mb point, you can try swapping the sticks around, or booting with only any one stick and then check if ubuntu works/loads fine. After all, 1Gb is plenty memory for Ubuntu.

Do post back with results;

---

### Post by dr.marc.byrd on 2008-07-23
Update:  Got new memory (2 @ 2GB, DDR2, 667), popped them in, all worked as expected - well not quite:  nvidia video driver problems.  But I'll try to figure those out myself.

Cheers & Thanks,


Marc

---

