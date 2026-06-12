---
title: "Sudden shutdowns after Gutsy Upgrade/ JBoss Install  - RAM related?"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Robsteranium on 2007-12-04
I've been running Xubuntu Feisty Fawn for a while.  I decided to upgrade to Gutsy last weekend.  The upgrade seems to have done some damage to my RAM that is causing sudden shutdowns (i.e. instant power-off without any warning),  Although the behaviour started during the upgrade I also suspect that the damage may have been caused by telling JBoss to take more heap space than I had spare RAM.

**The Problem**
The upgrade to Gutsy appears to have been a success (see background below) however I've since been plagued by sudden shut/ power-downs.  The problem doesn't seem to happen when I boot into Fedora Core 5 from another HDD.

I've narrow the problem down to the RAM chips since Memtest (from both the 7.10 disk and the 7.04 Live CD) causes the same shutdown problem.  I've since removed one of the two chips and the system seems stable (Memtest can complete a pass without the system powering down).

**The Questions**
Would problems with RAM cause these sudden power downs?
If this was a hardware fault why hasn't it occurred before (on Xubuntu 7.04 or FC5)?  Could the software be to blame?
Perhaps incorrect BIOS settings have caused this.

**Background**
Hardware:
ASUS P4SC Terminator
2 184-pin DDR DIMM slots:
- 128Mb, DDR, 333 SDRAM
- 512Mb, DDR

For some reason Memtest identifies the FSB at 100Mhz and consistently identifies 32Mb less RAM than expected (perhaps something to do with video shadowing)?

Software:
I set the gui upgrade manager running and left the room while it downloaded packages.  When I returned the system was shutdown completely (i.e. power-off).  Slightly perturbed, I booted the box up and discovered that the upgrade hadn't been completed.

I re-started the upgrade manager hoping to complete the "partial upgrade".  The upgrade process became stuck on several occasions.  Apparently these was some form of lock on a libpam module that would require a manual restart of some applications although the upgrade manager wouldn't tell me which.  In the end the solution was to Ctrl-C the error in the upgrade process (so that it would continue despite the lock) and repeated restart the partial upgrade until it revealed the applications I needed to restart manually.

I also installed a JBoss app server that repeating ran out of heap space.  I continued increasing the memory allocation (thinking that requirements beyond the available physical RAM would be supplied by the swap disk) and this lead to the same shutdown problems.


Sorry for the gargantuan post! :)  Any ideas/ suggestions appreciated.

---

### Post by inchaos on 2007-12-04
I've recently been having the same problem, my laptop randomly shuts off with no warning or shutdown sequence...then my HD makes that awful noise...

I didn't think that it could be RAM related but it makes a lot of sense, though I don't know how my RAM could have gotten damaged.  Your comp won't boot without RAM, you can't even get to the BIOS splash screen.  But if I had a problem with one RAM chip (I have two 1GB chips) wouldn't the other RAM chip keep my comp up and running?

I never thought to try the mem test, I'll do it as soon as I get home.

Now I'm afraid to use my computer until I figure this out.  I thought my laptop was overheating the first time it happened, but I have since installed the sensors applet and my CPU's are happy as can be when the problem occurs.  

How often does this happen to you?  So far I've only had it happen twice in the last week and I have my computer on for probably an average of 8 hours a day.

---

### Post by Robsteranium on 2007-12-05
I've replaced the RAM but this didn't solve my problem - the computer still switched itself off during memtest.

The problem was actually caused by a mis-specified BIOS setting: the memory speed-cpu speed ratio was incorrect.  Memtest now completes a full pass without any sudden shutdown.  Interestingly memtest still reports 100Mhz FSB (the new 3:4, cpu:memory ratio now provides an appropriate 133Mhz to my DDR 2100s).

It seems the upgrade was only the destructive test of the RAM and not the cause of the problem.

That's my problem solved... fingers crossed...


I presume your power connection/ battery are okay.

I've had a similar problem with my G4 PowerBook - the screen and cpu go dead but the DVD still spins (I'm blaming it on an OSX 10.5 Leopard upgrade!) .  If your HDD is grinding then perhaps this is the cause of the problem.  You could try booting from Live CD to test?

My problem only seemed to arise during RAM intensive operations (upgrading ubuntu/ starting JBoss) which is what alerted me to the cause.

---

