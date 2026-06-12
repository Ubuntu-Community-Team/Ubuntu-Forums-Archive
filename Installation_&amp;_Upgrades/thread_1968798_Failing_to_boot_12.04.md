---
title: "Failing to boot 12.04"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by j-dowsett on 2012-04-29
I'm wanting to install 12.04 on my desktop, which currently runs 10.04 quite happily.

I've used startup disk creator to make a live USB from the ISO image, and it boots fine on my laptop.  However, on the desktop the boot process halts with the screen full of text like:

> 
[    3.284008] Stack:
[    3.284008] Call trace:
[    3.284008] <IRQ>
[    3.284008] <EOI>
[    3.284008] Code: 4c 89 45 ....     
.
(3 lines of hex numbers)
.

[  299.834032] Stack:
[  299.834086] Call trace:
[  299.834128] <IRQ>
[  299.834238] <EOI>
[  299.834338] Code:
.
etc
.


I did notice that in each of the lists of hex numbers, a hex pair has < > around it.


I'm running a Gigabyte GA-MA69VM-S2 motherboard, with an AMD Athlon 64 X2 5200+ processor.

Can anyone suggest what might be causing this problem, and what I might be able to do about it?


Thanks
Joe

---

### Post by uncle hammy on 2012-04-29
I was battling the same issue (same MOBO) with Mythbuntu 12.04 and resolved it by disabling HPET in Power Management in the BIOS as per the last post here [http://ubuntuforums.org/showthread.php?t=1843810&page=2](http://ubuntuforums.org/showthread.php?t=1843810&page=2)

---

### Post by j-dowsett on 2012-04-30
Great, thanks, I'll give that a try when I get home.

---

### Post by j-dowsett on 2012-04-30
> **uncle hammy said:**
> I was battling the same issue (same MOBO) with Mythbuntu 12.04 and resolved it by disabling HPET in Power Management in the BIOS as per the last post here [http://ubuntuforums.org/showthread.php?t=1843810&page=2](http://ubuntuforums.org/showthread.php?t=1843810&page=2)

Excellent, thank you, that's done the trick :)
Just need to find some time to do an install now...

---

