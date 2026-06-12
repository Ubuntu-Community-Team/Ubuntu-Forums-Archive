---
title: "DVD Drive Issues, DVD's Not  Mounting... My Solution"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Therion on 2008-05-07
Posting this in hopes that it might help someone else so they don't have to go through as much as I did to find a solution.  First, here are the basics of what I did and what I was experiencing when trying to install Hardy Heron (64 bit):

I had a good burn of Hardy Heron 64-bit on known-good media.  MD5Sum confirmed... We're good to go.  The LiveCD spins up at boot and gives me the preliminary menu just like it should.  I hit Enter a couple times to accept English, American keyboard and so forth.  The CD spins up for a bit and then, suddenly, everything just stops...  No error messages, everything just sort of seems to quit working.

I reboot.  This time I remove "quiet" and kill off the splash-screen using F6 at the preliminary menu so I can see what's going on.  I find the following error -- which repeats itself about 100 times before dumping me out to BusyBox/Intramfs prompt:

[b]Ultra-DMA 32
End request I/O Error, dev SR0, sec 128
Logical Unit communications CRC error.[/b]

The syntax of the error may not be exact, but it's pretty darn close.

Switching DVD-RW drives does NOT help.  Both drives are KNOWN good-performers.


**Partial Solution #1:**  

I removed my DVD-RW and replaced it with a DVD-ROM drive.  Now I could install from the LiveCD but have NO optical drive support: I can't even READ factory DVD's; the drive is pretty much "dead" even though I see it listed in Places/Computer.


**Partial Solution #2**

Add **all_generic_ide** to the end of the kernel line after using F6.  This gets my DVD burner recognized and I can run the LiveCD normally.  This was a big improvement.


**Final Solution:**

I replaced the "old school" 40 connector/40 Pin cable with an *80 Connector/40 Pin cable*.  

**All problems resolved immediately after doing so.**

Hardy Heron booted off the LiveCD like a champ, installed flawlessly, recognizes the DVD-RW drive properly and plays & burns all optical media just as it should.  The cable cost me $5 at my local electronics warehouse.

For the more tech-challenged among us, here's [what an 80C/40P ATA cable](http://www.intel.com/support/processors/sb/img/atacable.gif) looks like.  Not so different.  Twice as many wires across the cable, but with the same number of pins as your old cable.

[Why this solution works](http://www.pcguide.com/ref/hdd/if/ide/confCable80-c.html), I guess...  I really don't know.  But here's hoping this information helps someone else.

---

### Post by lemming465 on 2008-05-10
The extra grounding wires reduce the electromagnetic noise from the rest of the system leaking onto the data lines of the cable.  Less noise means fewer data transfer errors.

---

