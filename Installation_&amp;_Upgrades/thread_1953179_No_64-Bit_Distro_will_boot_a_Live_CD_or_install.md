---
title: "No 64-Bit Distro will boot a Live CD or install"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by OliverHaslam on 2012-04-05
Hi

I'm trying to install Ubuntu 64-bit onto my machine, but the live CD will not boot. I get the keyboard logo on a purple background, and then a black screen with a blinking cursor. This is where it stays. I've left it ten minutes and it doesn't move. The disc spins down and the HDD light is off. 

I've tried the various options by pressing F6 but nothing seems to make it work.

I've also tried 11.10, 10.10 and even the latest beta, but they all do the same. I've tried Mint, too, and while that seems to be working, it eventually just sits there too. 

I have no such problems with the 32-bit versions. 

I am using an Intel E6600 Core 2 Duo in a Gigabyte P35C DS3R board with 8GB of RAM. 

Any ideas? I wanted 64 bit for all that RAM.

Cheers.

---

### Post by QIII on 2012-04-05
Intel graphics?

You may need to use the nomodeset option on boot.

I'm typing from a cell phone, so a bit hard to give detail.

Look up nomodeset in the search box upper right.

---

### Post by OliverHaslam on 2012-04-05
> **QIII said:**
> Intel graphics?

You may need to use the nomodeset option on boot.

I'm typing from a cell phone, so a bit hard to give detail.

Look up nomodeset in the search box upper right.

Nope, Nvidia. I've tried nomodeset too.

---

### Post by OliverHaslam on 2012-04-06
Post update: I've had the new RAM running through Memtest for about 12 hours and that's all OK so far, so that's that.
 
I did wonder if the reason I am struggling with a 64bit install is the fact it's hitting all the RAM, whereas the 32Bit isntalls are obiously only hitting one stick of 4GB.
 
Interestingly, I couldn't get the PAE Kernel for the 32Bit to run properly when I tried the other day, either, though that was not a fresh install and may be unrelated.
 
Does Ubuntu do any memory checks right at the beginning of booting?
 
I'll try it with one stick of RAM in tonight to rule that out.

---

