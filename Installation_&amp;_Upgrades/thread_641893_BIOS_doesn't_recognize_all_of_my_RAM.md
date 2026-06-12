---
title: "BIOS doesn't recognize all of my RAM"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by aristachus on 2007-12-16
My Asus M2N32 WS Professional motherboard BIOS doesn't recognize my upgrade from 2GB of RAM to 4GB of RAM.  I have tried upgrading the BIOS to see if it changed or gives me more options, but was unsuccessful in this attempt.  It supports up to 8GB of memory, and so 4 should be fine.  (I have 4 1GB ddr2 sticks (2 are 800, the other 2 are 667).  Any help would be greatly appreciated, thanks.

---

### Post by src2206 on 2007-12-16
Only 64bit versions (and Vista 32 bit) are able to use and recognize >3GB of RAM. It is a limitation related to Physical Address Extension. Look in your Motherboard manual, it should be mentioned there. :)

---

### Post by aristachus on 2007-12-16
I've got 64-bit gutsy installed as my primary OS (dual booted with 32-bit xp for the odd game of worms), and know that the other operating systems can't recognize all of the RAM, I'm just confused as to why my bios doesn't recognize any of it.  There doesn't appear to be any options in there dealing with memory mapping or the memory hole that I can find.

---

### Post by src2206 on 2007-12-16
Ok, try to get CPU-Z (sorry you need to run this in M$ Windows and I am yet to find an equivalent alternative for Ubuntu yet).
As you run CPUZ, go in the Memory section and see the reports in the slots. If slots are showing all the modules then the problem lies in some place else.

---

### Post by aristachus on 2007-12-16
My BIOS only recognizes 2GB of RAM, the other 2GB don't claimed to be installed in the BIOS setup, nor do they show up in CPU-Z.  I need a way of somehow forcing my BIOS to recognize all of the RAM, it says that only 2GB are installed.  I have tried upgrading the BIOS, and had no luck that way either.

---

### Post by src2206 on 2007-12-16
What is the make and model of your MB? How many RAM slots you have? What is the size and type of each RAM module?

Please let me know.

---

### Post by aristachus on 2007-12-16
The motherboard is an Asus M2N32 WS Professional which has 4 RAM slots DDR2 800/667/a few others that don't matter for the sake of this post, all of which currently have a 1GB stick in them.
Specifically, the original 2GB are a set of paired 800mhz OCZ DDR2 Gold Rev2 XTC ([http://www.canadacomputers.com/main.php?do=ShowProduct&cmd=pd&pid=015371&cid=RAM.346.307]("http://www.canadacomputers.com/main.php?do=ShowProduct&cmd=pd&pid=015371&cid=RAM.346.307"))
The newly installed RAM is 2 1GB sticks of PNY DDR2 (PC2-5300) optima memory.  Athlon 64 X2 5000+ processor.

---

### Post by src2206 on 2007-12-17
So you have a RAM frequency mismatch. The newer ones are 667MHz whereas the older is 800MHz. Furthermore, if I remember correctly, your board (which is somewhat similar to mine) can not support any thing more than 4GB when you use 800MHz RAM.

I think that your trouble is sourced from the mismatch.
I suggest that you consult your MB manual.

---

### Post by aristachus on 2007-12-18
I tried setting the timing manually in my bios to 667mhz in the event that such an issue existed before I installed it, and then back to normal later without luck.  It should still recognize it is there, not necessarily be usable but it should be recognized.  I also borrowed some of my roommates RAM which is 667, and replaced my 800mhz with that, it still only recognizes 2GB.

---

### Post by src2206 on 2007-12-18
Then I suggest that you get in touch with ASUS immediately...as this should not happen. :?:

Sorry I could not be of much useful assistance. :(

---

### Post by jeffreytp on 2008-04-05
I am having a similar problem.  Did you ever find the solution?

---

