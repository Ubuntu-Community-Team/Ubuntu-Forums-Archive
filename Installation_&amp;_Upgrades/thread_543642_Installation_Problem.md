---
title: "Installation Problem"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by IainR on 2007-09-05
Trying to get up and running on a Dell Latitude CPx with 6MB hard drive and 384 RAM.

As Ubuntu is trying to load I get following message:

Buffer I/O error on device fd0, logical block 0

Ususally get this twice, then:
hdc : timeout waiting for DMA
Buffer I/O error on device hdc, logical block 0
repeated for logical blocks 1 to 7

Any ideas?

Regards,
Iain Reeves

---

### Post by wonk-o-matic on 2007-09-05
On my dell, I booted from the CD, then pressed F6 and used the options: 

vga=771 noacpi noapic nolapic

I don't think that they all proved necessary, but it go me started.

---

### Post by IainR on 2007-09-05
Still get the error messages.  This laptop used to run NT 4.0.  It does seem to mess up a number of things.  Could it be the root of my current problems?

---

### Post by merlinus on 2007-09-05
Your hdd may have defects, given the error messages.

-merlin

---

### Post by IainR on 2007-09-06
I have previously installed and run W*nd?ws XP Pro with no apparent problems, but I'm not inclined to pay Microsoft any more money to use it on this old machine!.  

I have also run a hard disc diagnostic tool obtained with PC Beginner and no errors are detected.

The HD in question is a Fujitsu MHK2060AT.

---

### Post by wonk-o-matic on 2007-09-06
What was I thinking?  

The fd0 stuff caught my attention, and I missed the *hdc*, which is probably your CD rom.  

A number of things can cause this.  It's possible that you have hardware trouble or even a bad CD, but most likely you need to add this parm when you boot: 

ide=nodma

---

### Post by IainR on 2007-09-06
I don't seem to get far enough to see any boot prompt.

I get to the first menu and select install.  Then about 90 seconds of watching the logo with oscillating orange bar.  Then a blank screen and the error messages start to appear.

---

### Post by merlinus on 2007-09-06
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by wonk-o-matic on 2007-09-06
DON'T choose install.  Press F6, then type your additional boot parameters.

---

### Post by IainR on 2007-09-07
OK, went for f6 and added ide=nodma at the end of the boot option string.

Got the same two fd0 error messages, then CD runs for a bit and it looks as if something positive is happening.

Time for a beer and sit back to see what happens!

Watch this space.

---

### Post by IainR on 2007-09-07
That's it, up and running.  Thanks for your help.:)

---

