---
title: "Just can't boot from the Ubuntu boot cd"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by werg on 2008-01-13
Hi, I have been unsuccessful in my attempts to install Ubuntu on my laptop. It's a 32 bit base machine, and I downloaded the image file accordingly. I've checked the BIOS and everything is in order; the CD drive is in first booting rank and CD booting is enabled. I've tried two different CDs with the same result. Whenever I boot my laptop with the CD in, there will be a black screen for about 2 minutes and then Windows load with the message that there has been an error, proposing to run a diagnostic. I can't access the Ubuntu installer at all. Any idea of what the issue might be and how can it be solved? Thanks.

---

### Post by Partyboi2 on 2008-01-13
try burning at a lower speed x4 or lower
check the md checksum as well, if you have not already done so.

---

### Post by linuxisfree on 2008-01-13
Also, just in case, can you post the specs of your computer? Thanks!

---

### Post by whYME953 on 2008-01-14
Hi,

I'm having the same problem. (This is my first attempt at installing Linux)

I have a Dell Inspiron e1505 
intel core 2 duo T7200  2.00 Ghz
2 Ghz RAM

I partitioned my hard drive in order to do a dual boot with windows. My computer will not recognize the CD at all, it will not boot from the CD (same symptoms as the original poster) and I cannot access the CD through windows. (xp media center edition)

The CD runs fine on my desktop.

edit: I'm Installing ubuntu 7.10 from a CD I got mailed

edit 2: Actually, My symptoms are not quite the same as werg's, I didnt read it right the first time around... 
after that initial blank period my computer is loading windows without any problems.

---

### Post by linuxisfree on 2008-01-14
> **whYME953 said:**
> Hi,

I'm having the same problem. (This is my first attempt at installing Linux)

I have a Dell Inspiron e1505 
intel core 2 duo T7200  2.00 Ghz
2 Ghz RAM

I partitioned my hard drive in order to do a dual boot with windows. My computer will not recognize the CD at all, it will not boot from the CD (same symptoms as the original poster) and I cannot access the CD through windows. (xp media center edition)

The CD runs fine on my desktop.

edit: I'm Installing ubuntu 7.10 from a CD I got mailed

edit 2: Actually, My symptoms are not quite the same as werg's, I didnt read it right the first time around... 
after that initial blank period my computer is loading windows without any problems.

Your specs seem good... so, your Windows does not see the cd? Try any other cd... (try more than 1, in fact)... if THAT can't be accessed as well, then your problem is most likely the cd drive... if it works... we'll think of something...

EDIT: that is... try those cds in your windows partition...

---

### Post by Partyboi2 on 2008-01-14
Did you burn the ubuntu image as a iso not as data?

---

### Post by themad on 2008-01-14
On my Dell laptop to boot from CD, you have to restart it before booting. So U have to start laptop and then pres ctrl+alt+del.
If not try to download Ubuntu image again.

---

### Post by devoncatt on 2008-01-14
Some Dell machines require you to enter F12 at boot to choose the boot medium. The default is the hard drive. Have you checked the BIOS to verify or change boot order?
Devoncatt

---

### Post by linuxisfree on 2008-01-14
> **devoncatt said:**
> Some Dell machines require you to enter F12 at boot to choose the boot medium. The default is the hard drive. Have you checked the BIOS to verify or change boot order?
Devoncatt

he did. just check the first post. it has been set that the cd boots first. :D

---

### Post by whYME953 on 2008-01-14
I got mine working.
I downloaded and burned a new disc image which worked fine. Go figure...
Thanks anyways.

---

### Post by linuxisfree on 2008-01-15
Congratulations! Glad you got it working!:D

---

