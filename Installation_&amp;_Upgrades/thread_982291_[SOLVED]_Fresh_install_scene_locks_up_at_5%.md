---
title: "[SOLVED] Fresh install: scene locks up at 5%"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Guitar John on 2008-11-14
I am attempting to do a fresh install of Ubuntu after my [earlier woes]("http://ubuntuforums.org/showthread.php?t=979707") with a kernel panic.  Just because I [read somewhere]("http://kmandla.wordpress.com/set-up-ubuntu-for-speed/tips/blank-the-drive/") that it was a good idea, I blanked the drive using [DBAN]("http://www.dban.org/").  Interestingly, with that process I got a kernel panic on the first pass.  It is supposed to do three.

But the install disk showed a blank drive so I decided to give it a try.  Three install attempts later (using three different cd's), here I am asking for help.  The live cd runs fine, so I am inclined to think that if this is a hardware issue, it is the hard drive rather than memory but I am prepared to be wrong on this one.

FWIW, I ran a hard drive diagnostic in the BIOS and it passed.

Basically, after all of the local configuration install screens, I hit the install button.  The bar makes it to 5% 
```
**Partitions formatting**
Creating ext3 file system for/in partition #1 of SCS13 (0,0,0) (s...

```
and then the screen locks up.

Any help is always appreciated.  
Thanks.

---

### Post by cariboo on 2008-11-14
Have you tried any of the **apic** options available by pressing F6 at the menu screen?

Jim

---

### Post by wpshooter on 2008-11-14
Have you checked the integrity of the Ubuntu CD by runnnig the verification function that is found on the initial Ubuntu boot screen menu ?  My guess is that you have, but thought I would ask.

Are you burning the CD that 4X or slower ?

---

### Post by Guitar John on 2008-11-14
wpshooter,
Yes to all.  Actually, one of the install disc's was an "Official" disc -- the ones they send you in the mail.  That was version 8.04.  The other 2 were Ubuntu 8.10 and Xubuntu 8.10.

cariboo907,
I'm looking at those now.  The options available are:
[LIST]
[*]acpi=off
[*]noapic
[*]nolapic
[*]edd=on
[*]Free software only
[/LIST]

Other than the last one -- which is self explanatory -- I have no idea what they do.

---

### Post by Guitar John on 2008-11-14
Further update:
I tried formatting the hard drive to ext 3 using GParted from the live cd.  Same thing.  I click *Apply* and the screen locks up.

Corrupted hard drive?

---

### Post by wpshooter on 2008-11-14
Have you tried installing using safe graphics parameter ?

If that does not work, then try installing from the ALTERNATE (text based) CD.

Good luck.

---

### Post by Guitar John on 2008-11-15
I may have bigger hardware issues than I had previously thought.  I am running *memtest 86+* from the live cd.  It is currently 39% through the 3rd pass and showing 4.9 MILLION Errors.  :shock:

```
Memtest86+ v2.01           |  Pass 5% #
Pentium 4 (0.09) 2793 MHz  |  Test 39% #########
L1 Cache: 16K 17135 MB/s   |  Test #3 [Moving inversions, 8 bit pattern]
L2 Cache: 1024K 17135 MB/s |  Testing: 140K - 2048M 2550M
Memory: 2550M 2598 MB/s    |  Pattern 20202020
Chipset: Intel i915P/G (ECC: Disabled) - FSB : 199 MHz - Type : DDR-II
Settings: RAM: 266 MHz (DDR532)/CAS : 4-4-4-12 / Dual Channel (Interleaved) 
```

---

### Post by wpshooter on 2008-11-16
> **Guitar John said:**
> I may have bigger hardware issues than I had previously thought.  I am running *memtest 86+* from the live cd.  It is currently 39% through the 3rd pass and showing 4.9 MILLION Errors.  :shock:

```
Memtest86+ v2.01           |  Pass 5% #
Pentium 4 (0.09) 2793 MHz  |  Test 39% #########
L1 Cache: 16K 17135 MB/s   |  Test #3 [Moving inversions, 8 bit pattern]
L2 Cache: 1024K 17135 MB/s |  Testing: 140K - 2048M 2550M
Memory: 2550M 2598 MB/s    |  Pattern 20202020
Chipset: Intel i915P/G (ECC: Disabled) - FSB : 199 MHz - Type : DDR-II
Settings: RAM: 266 MHz (DDR532)/CAS : 4-4-4-12 / Dual Channel (Interleaved) 
```

Have you tried re-seating your memory.

I would then try testing with the a downloaded version of the latest version of memtest.

---

### Post by Guitar John on 2008-11-16
I haven't done it yet, but I was going to try removing each of the pairs and re-running the test.  I guess that while I'm in there, re-seating them would b a logical first step.

I'll let you know.

---

### Post by Guitar John on 2008-11-16
The computer came with 512 MB RAM (2 x 256).  Sometime later on, I add 2 GB (2 x 1) for a total of 2.5 GB.  I pulled out the 2 newer ones first since they came from an online vendor.  Same results.  

I then pulled the 2 original ones and replaced them with the two 1 GB chips - so they would be in slots #1 & 2.  I re-ran the test.  Golden!!!

I booted to the live CD and checked the *System Monitor*.  It showed *Memory: 2 GB*.

I clicked *Install*......

.....\\:D/

Maybe someone can explain this to me, but if not I am happy to once again have a working system.

---

### Post by wpshooter on 2008-11-18
> **Guitar John said:**
> The computer came with 512 MB RAM (2 x 256).  Sometime later on, I add 2 GB (2 x 1) for a total of 2.5 GB.  I pulled out the 2 newer ones first since they came from an online vendor.  Same results.  

I then pulled the 2 original ones and replaced them with the two 1 GB chips - so they would be in slots #1 & 2.  I re-ran the test.  Golden!!!

I booted to the live CD and checked the *System Monitor*.  It showed *Memory: 2 GB*.

I clicked *Install*......

.....\\:D/

Maybe someone can explain this to me, but if not I am happy to once again have a working system.

Probably as simply as the old and new memory modules were NOT compatible.

Good computing.

---

