---
title: "Linux won't install on new PC :(  AMD-64"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by chris191 on 2010-09-03
[INDENT]Hi,
I'm but I'm having problems installing Linux. Both Ubuntu 10.0.4 and Mint freeze after going through the initial install options, setting partitions and starting the install at around 5%
 
It just jumps to back screeen, with Ubuntu logo and 5 red dots..
 
I've tried d/l different versions and burning new DVDs.
 
Anyone have any ideas?

My Spec is: 
[LIST]
[*]AMD PHENOM II X4 955 (3.20GHz/8MB CACHE/AM3) - BLACK EDITION
[*]ASUS® M3N WS: DUAL DDR2, S-ATA II, 2 x PCI-Ex, 2 x PCI
[*]8GB CORSAIR XMS2 DUAL-DDR2 800MHz - LIFETIME WARRANTY
[*]300GB WD VELOCIRAPTOR® SATA 3-Gb/s, 16MB CACHE (10,000rpm)
[*]500GB SERIAL ATA 3-Gb/s HARD DRIVE WITH 8MB CACHE (7,200rpm
[/LIST]*Note: PC came with Windows 7 Home (and that worked fine) so I don't think its a HD problem*
 
Thanks. 
[/INDENT]

---

### Post by chris191 on 2010-09-03
Just to add...
If I select ReiserFS instead of ext4 it gets much further and starts copying files but stops at 35% with an error 5 I/O stating a problem with CD/DVD or faulty H/D. I hv tried 2  DVDs now and have same problem.
 
Only thing I have not done is to burn a new DVD at a lower speed.

---

### Post by thatguruguy on 2010-09-03
I've had, at best, mixed results when trying to install from a CD.  Have you tried to install from a USB stick instead?  I've had much better results that way.

---

### Post by coffeecat on 2010-09-03
> **thatguruguy said:**
> I've had, at best, mixed results when trying to install from a CD.  Have you tried to install from a USB stick instead?  I've had much better results that way.

I think you're in a minority with your CD experience. I've been installing various flavours of Linux with CD/DVDs for over 5 years now and rarely had a problem. Although I agree that bootable USB sticks are much more convenient. 

@chris191, two things you don't mention and which are vital. Did you check the md5sum of the downloaded ISO? And did you do a disc integrity check when you first booted the CD? It's in the menu somewhere. You're right to try burning at a lower speed but don't forget those two checks.

Also try a different brand of CD/DVDs. Some drives seem to be fussy about this. This may be the reason for thatguruguy's experience.

---

