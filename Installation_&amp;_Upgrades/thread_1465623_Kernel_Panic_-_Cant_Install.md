---
title: "Kernel Panic - Cant Install"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by nexoncore on 2010-04-29
When I load the live CD into my computer, the DVD drive spins very fast and then drops down to command lines with a kernel Panic. I have tried with the Final Release and with the Release Candidate. Because of this I cant even load up to the live CD enviroment.

It also mentions the name of my mother board in the code, the motherboard is a gigabyte G41M-ES2L and is brand new.

Could someone give some advice or help? Currently I dont have ubuntu installed on this computer as I went for a fresh install with vista.

---

### Post by drreed on 2010-04-29
That sounds like bad cd's, 

What happens if you "put the cd in" another computer? Where you running Windows when this happened, or did you put the cd in and then boot? Are you using Wubi? What version is this? I've never used Wubi so ignore my advice till you check with others.

If you burned the cd's, then make sure you did this:

1. Downloaded iso file and verified the checksums to insure your download wasn't corrupted..

Only after you've done step 1 . . .

2. Burn the iso to a cd, shutdown, boot with the cd in the computer, and when the first screen comes up choose "Test CD for defects"

Only after you pass steps 1 and 2 should you try to install.
Give us some more info and we might be able to give better advice.
:P

---

### Post by P4man on 2010-04-29
You may also want to run memtest, just to make sure...

---

### Post by nexoncore on 2010-04-29
I am experienced installing ubuntu and have installed ubuntu 10.04 RC on this computer before but it recently had a new motherboard put in after the onboard GPU failed. This model is different to the origional.

Referring to the download today, I can not say if its corrupted or not and have no other PC's to test with. But the Release Candidate CD I have installed on this computer prior the motherboard change and it worked fine then, but it doesnt now. I also checked the RC CD for damage, but the CD is clean as I keep all burned CD's in jewel cases.

I am going to try from live USB now and see how that works.

---

### Post by nexoncore on 2010-04-30
The CD was fine and Memtest was fine, decided to do a blind install without using the live CD enviroment which went perfectly.

---

