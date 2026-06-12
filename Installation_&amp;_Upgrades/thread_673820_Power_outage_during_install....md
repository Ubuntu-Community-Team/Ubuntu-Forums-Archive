---
title: "Power outage during install..."
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by jb584 on 2008-01-21
So I downloaded ubuntu and burned it to a cd.  I put the cd in my desktop and was running it, I selected install/run and it went to a screen with a bar moving back and forth.  While on this screen the power went out and thus my computer turned off.  When power was restored all my computer will do is make a long beep and then beep again and again.  It doesn't load anything, just beeps.

Any suggestions would be helpful.

---

### Post by Partyboi2 on 2008-01-21
when you say it doesn't load anything, I am guessing that you have windows installed on the pc as well and you are unable to boot into that as well. Is that correct?

---

### Post by tanu_10 on 2008-01-21
Is it on the windows system?

same thing happened to me, while i was installing ubuntu 7.10 on my windows system. later, after power on, it was not able to boot in windows also. it will just hang on, without any boot up.

then i run the installation CD again and tried to boot up in windows first.
When you run the ubuntu CD, You need to set the windows boot up flag in the administration tools.  In the administartion tools -> partition table - > select the flag box for windows boot up. Then restart the computer. Then it will boot up in windows. later again u install ubuntu, as initially installation will not be complete.

---

### Post by jb584 on 2008-01-21
No it doesn't have windows on it.  I just replaced the HD on it and couldn't find the recovery disk, so I was going to install this until my recovery disks came. It appears that it was a bad idea...

---

### Post by jb584 on 2008-01-21
I guess I will give system info in case that might help...

MB: XTX 780i
CPU: Intel Core 2 Quad
RAM: 4 GB DDR2
HD: Seagate 500
Graphics: Gforce 8800 GTS
Sound: Audigy 2 Soundblaster

---

### Post by Partyboi2 on 2008-01-21
The only thing I can think off is to find out more about the beeps. Check the manual for your board and see what that beep code could mean. Different beeps mean different things.

---

### Post by torgrot on 2008-01-21
Can you boot off the LiveCD?  If not can you get into the bios?  Those would be my first two steps.  

torgrot

---

### Post by jb584 on 2008-01-21
Well, I called tech support for my MB this morning and a stick of ram went bad.  So now i just need to figure out which...

---

### Post by az on 2008-01-21
The problem was caused by the power outage, and not Ubuntu.

Use memtest86 (on the Ubuntu disk) to check your ram.  Remove the first stick and try to boot.  Often, your computer will boot with faulty ram if the first few Kb are okay.  Memtest86 needs only a very small amount of ram to runction to be able to run.  Since your computer won'T boot with both sticks in, I would think it's more likely that the first stick is the one that's bad.  The fitst stick is usually the one that'S closest to the CPU.

---

