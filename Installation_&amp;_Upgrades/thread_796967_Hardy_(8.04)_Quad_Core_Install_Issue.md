---
title: "Hardy (8.04) Quad Core Install Issue"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by handleyj on 2008-05-16
So I built/bought a new machine:

Intel Q9300 (hand-me-down -- well tested, known good)
2x2GB (4GB total) DD2-800 RAM (hand-me-downs -- well tested, known good)
XFX nForce 630i motherboard with 7150 (onboard video) - (brand new)
SoundBlaste Live! (hand-me-down, known good)
WD1600 160GB Hard Drive (hand-me-down, known good)
Sony DVD+-RW (brand new)
CoolerMaster 650W PSU (brand new)

Spent a few hours getting all the hardware put together.  Popped in the Ubuntu 8.04 i386 Alternate CD (I'll need the RAID install support eventually - but I wanted to do a test install with just the above configuration).  And it gives me the first menu, and I select "Install Ubuntu."  And then the screen goes black except for a little blinking cursor in the upper left corner.  That's it.  No messages, no nothing.

So I start fiddling with things.  I removed one of the RAM sticks, no good.  I tested the Ubuntu CD, it passes the tests successfully.  None of these changes the symptoms.  I tried the Ubuntu CD on another machine (680i mobo & Q9450 & 8800GTS), and it installs fine.

So I figure maybe the motherboard is bad.  So I go ahead and run MemTest, figuring it might fail on a bad mobo.  But it runs and runs and runs (for just over 8 hours).

Well then, I start to fiddle in the BIOS.  And lo and behold, when I turn off the "multiple processing" for the CPU, the install runs and succeeds.  I am right now typing this on my brand new installation of Ubuntu 8.04.

BUT!

I'm only using 1 of my 4 CPU cores!  Ugh!  And when I go re-enable the "multi processing" feature in the BIOS, the system just hangs at the same black screen with a little blinking cursor ... right after GRUB finishes it's countdown to boot.

help...

-joe

---

### Post by handleyj on 2008-05-16
Actually, I just tried enabling it in the BIOS again, and it does say:

Starting up...
Please wait...

Right after the GRUB countdown. But then it hangs. During a normal boot, right after that, the lights on my mouse and keyboard (both USB) would flash, then the Ubuntu boot progress page would appear.  Neither of those things happen when I have all four cores enabled in the CPU.

Thanks for any help!

-joe

---

### Post by handleyj on 2008-05-17
bump ... :(

---

### Post by Em-Buntu on 2008-05-17
I'm not certain, but it would seem to me if you want smp and numa support, you need to run the x86-64 kernel rather then the i386 (single core) kernel.

I'm running a quad Opteron (2x dual cores) and always use the x86-64 CD.
The system sees and uses all 4 cores.

---

### Post by undecidable on 2008-05-18
As another data point,
I am using 32 bit Kubuntu 8.04
on a dual xeon (each single core) setup with no problems.

At the end of this week I will be installing on a dual xeon dual core setup (ie 4 cores).  Will try to report back next week.  

One think you might consider is to turn off quiet in grub's menu.lst (both in the kernel line and in the by itself line) so you can see where it is hanging.  

MC

---

### Post by handleyj on 2008-05-18
Well I tried the 64-bit version of Ubuntu, and it hung during installation at the exact same spot.  Also, I am running Kubuntu i386 7.04 on a AMD dual-core, and both cores are recognized and used, so I don't think that's the issue here.

I also tried to install Fedora 9, and it also hung during installation.  It at least spit some text onto the screen, it got to "/sbin/loader" and then hung.  My feeling is that once you see a message on the screen, that was successful, so whatever the command that runs after /sbin/loader is the one with the problem ... but that's just a theory.

Anyway, I'm not sure that it matters.  I removed the motherboard, and plan to return it and get a new one with a different chipset.  Maybe an Intel G33 or something.

---

### Post by handleyj on 2008-05-20
So I returned the nVidia based board, and got an Intel branded board with a G35 chipset.  Ubuntu installed and runs with no problems and with all 4 cores activated.

I was also able to install onto an nVidia based i680 board.  So I'm thinking the problem with the last board was the 7150 chip...

Anyway, I guess I'm up and running at this point, but it's too bad I couldn't get that board to work.  I really liked the feature set much better than this new Intel board, but of course, the feature of actually working trumps the others.  :-)

---

### Post by s_raghu20 on 2008-09-17
> **handleyj said:**
> So I returned the nVidia based board, and got an Intel branded board with a G35 chipset.  Ubuntu installed and runs with no problems and with all 4 cores activated.

I was also able to install onto an nVidia based i680 board.  So I'm thinking the problem with the last board was the 7150 chip...

Anyway, I guess I'm up and running at this point, but it's too bad I couldn't get that board to work.  I really liked the feature set much better than this new Intel board, but of course, the feature of actually working trumps the others.  :-)

Guys, might be a naive question, but I have to ask it anyway.

I've recently put together a Intel Quad core Q6600 with 2 GB RAM(800 MHz) and an intel DG33 motherboard.  All was fine with Live CD and installation both. I am running the following - 

```
raghav@deskubuntu:~/cprgs$ uname -a
Linux deskubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

```

The question I want to put across is, How do I know for SURE that my os - system is actually Using the four cores that the hardware is providing.  Does the fact that System Monitor shows me 4 CPUs enough ? Or do I need to do/configure/check something else to be sure ?

I have always wanted to see (thats still a question as to how would I do that) the real effect of multiple cores on a given set of software.  I guess this is my very first step, towards understanding.  I believe the OS has to be aware that there are four cores and they allow parallel processing before any application can start using the benefit of that.

any pointers would be helpful.

regards
raghav..

---

### Post by katon on 2008-09-24
have you resolved the problem?

---

### Post by marceloguedes on 2009-04-27
Hi. I had the same problem with the same version of Ubuntu. The reason was the version of the kernel. One of the automatic updates installed the 386 serie of the kernel instead of the generic.
For a quad-core, or dual-core, the correct kernel is the generic. For example:
$uname -a
Linux <machine_name> 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

Here, the apt-get system had installed the 386 version. Using the uname probably you will see something similar to it:
$uname -a
Linux <machine_name> 2.6.24-23-386 Wed Apr 1 21:30:02 UTC 2009 386 GNU/Linux

I removed the 386 version from grub and ran the system with the generic and all the 4 cores here was used.

An easy way to see the cores is using the software ksysguard. The software have to show each one of the CPUs in you tree list like: CPU0, CPU1, CPU2, CPU3 for a quad-core. If you get in ksysguard and see only one (CPU0), probably you have this issue in your computer.

I expect that this information helps.

---

