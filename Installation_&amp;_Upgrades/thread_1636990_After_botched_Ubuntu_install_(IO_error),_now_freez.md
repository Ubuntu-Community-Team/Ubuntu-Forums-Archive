---
title: "After botched Ubuntu install (IO error), now freezes at slpash screen"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by usopenplayer on 2010-12-03
Hey Guys,
  I am installing Ubuntu 10.10 i386 on a friends laptop (her Vista partition was ridden with viruses).

She has a Toshiba Satellite 
Model#: PSAG8U-04001W


It originally booted into Ubuntu without any problems, I deleted her windows and recovery partitions with gparted, and copied all of her important files to an NTFS partition at the end of the drive. I also left a 1.6GB Toshiba partition at the beginning of the hard drive. I wasn't sure what it's for so I just let it be.

I then initiated the Ubuntu install and about halfway through it bombed out with an IO error, I wasn't able to write the specific error down.

Now her computer refuses to boot past the initial splash screen:
I can run "Test Memory" but when I select "Try Ubuntu without Installing", "Install Ubuntu", or "Check Disk for defects" it locks up for 5 minutes, and eventually begins outputting the weirdest green colored text error that I have ever seen.

the text font is a little messed up but it says something like: "ENN: Error AAAA reading xnclnr AXXX"
Those trailing XXXs change with every newline of the error.
The install disk was already corrupted and I have tried switching her hard drive from AHCI to Compatibility mode, and even burned a new disk just for good measure.

I am now at a loss... can anyone help me out here.

---

