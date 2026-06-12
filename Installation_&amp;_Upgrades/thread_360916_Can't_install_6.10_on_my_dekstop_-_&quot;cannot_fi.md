---
title: "Can't install 6.10 on my dekstop - &quot;cannot find/mount CD-ROM&quot;"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Vivix729 on 2007-02-13
I installed 6.10 on my laptop, and since I am so impressed, I decided to make a dual boot system on my desktop.  I have two 300 gig SATA drives, and I thought I'd just keep Windows on one and Ubuntu on the other.

However, when I used the DVD to see the hardware compatibility, the loader would hang right after the Ubuntu screen.  I also noticed the DVD drive stopped spinning.  Hmm...then I tried Kubuntu.  Same thing.

Then I decided to use the text installer.  Then the problem was obvious.  When it tried to mount the DVD drive, it just couldn't detect it???

Any ideas?

My config:

Core 2 Duo 6300
Intel Motherboard
1 Gig ram
Lite-On DVD burner

---

### Post by Kateikyoushi on 2007-02-13
Is that a Sata dvd drive ?

---

### Post by Vivix729 on 2007-02-13
No, it's an IDE.  I just found the info in the wiki.  My motherboard is the issue (well that and the IDE drive).  Guess this installation is gonna wait a little bit :(

Once I install it and upgrade to the newest kernel, I shouldn't be experiencing issues such as these, right?

---

### Post by Kateikyoushi on 2007-02-13
After the kernel suports your chipset or motherboard it should work.
Did the wiki mention which kernel does support your mobo ? Currently edgy uses 2.6.17.11
I don't know which kernel is in feisty currently but you could try a herd disc of the next version of ubuntu that might already support it, of course being still in development won't be as stable as current releases.

---

