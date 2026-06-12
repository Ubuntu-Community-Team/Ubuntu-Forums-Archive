---
title: "Ubuntu 7.10 RC Install Help"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by Muhahahahaz on 2007-10-14
By the way, **I am no longer talking about the RC!**  I tried to edit the title, but it doesn't change on the thread list.  I can install the 32-bit no problem, but 64-bit is not working.  I also have Vista Ultimate x64 installed, so I know that my hardware is capable.

I get to the first screen where you choose how to boot from the CD, so I choose the first one.  After that it says something about loading the kernel, but then the screen goes blank and nothing appears after that.

I checked the MD5 sum of both the ISO file and the CD after it was burned, and they both checked out, so I don't know what is going on. :(

Here are my specs:

Gigabyte P35-DS3R Motherboard
Intel Q6600 G0 CPU
2x1GB G.Skill HZs, DDR2 800MHz
NVIDIA 8800GTX
etc...

I'm using the 64-bit ISO.

Any help would be greatly appreciated.  Thanks! :D

---

### Post by Muhahahahaz on 2007-10-19
Anyone??

I have also tried the official release now, and I get the same thing.  The MD5 sums are correct and everything.

The DVD drive does spin for quite some time after the screen goes blank, but after maybe 10 minutes there is no more activity.

This makes me very sad. :cry:

---

### Post by Muhahahahaz on 2007-10-21
I have the 32-bit version working.  What's the deal with x64? :(

---

### Post by milkrock on 2007-10-21
I'm running into the same issue, I can boot the 32 bit disc but not the x64 disc, I'm on an intel 6600 (dual core 64bit capable) as well so maybe cpu related? I also have a very similar video card, nv 8800 gts (from which I understand has similar issues to the 8800 gtx in many games 2gigs of ram, and an Asus motherboard. Any information from other users would be helpful

---

### Post by TheConqueror on 2007-10-22
There seem to be a lot of posts relating to issues of black screens.  I have an almost the same configuration nv 8800gts, E6600, 2GB.  But other people are reporting the same issues with ATI cards.  Just search the forums for "black screen".

---

### Post by Homeskillet on 2007-10-22
I'm having the same trouble.  I have an E6750 and a 8800GTS.  However, my first thoughts were to blame my new P35 chipset on my ASUS motherboard.  I also can't get WinXP 32bit to load the setup (blue screens - its really quite cute), again another reason for me to blame the P35 chipset.  Thoughts?

---

### Post by Muhahahahaz on 2007-10-23
Well, both Vista Ultimate x64 and Gutsy x86 work fine for me, so nothing is wrong with my hardware.

Of course, that's not to say it isn't related to the hardware.  Perhaps Gutsy x64 doesn't like my hardware.

---

### Post by TheConqueror on 2007-10-25
Well I have mine working.  All I had to do was change the 'splash' to 'nosplash' at the startup (F6 on the LiveCD).  Then in Grub I have changed the main boot line to also say 'nosplash'.

I'm wondering if it's my monitor.  I have a 22" widescreen monitor with a native resolution of 1680x1050.  I have seen other people post messages with this sort of monitor having trouble.

---

### Post by Muhahahahaz on 2007-10-25
I also have that size and resolution for my main monitor.  Previously I have been getting a lower resolution while installing from the live CD, but perhaps Gutsy has problems.  I will try nosplash when I get home.

---

### Post by Muhahahahaz on 2007-10-25
Wow, "nosplash" worked great.  Thanks!

Now I have everything in 64-bit on my machine. :D

(At least the OSes anyways... still waiting for all programs to switch ;))

---

### Post by Em-Buntu on 2007-10-25
> **Muhahahahaz said:**
> By the way, **I am no longer talking about the RC!**  I tried to edit the title, but it doesn't change on the thread list.  I can install the 32-bit no problem, but 64-bit is not working.  I also have Vista Ultimate x64 installed, so I know that my hardware is capable.

I get to the first screen where you choose how to boot from the CD, so I choose the first one.  After that it says something about loading the kernel, but then the screen goes blank and nothing appears after that.

I checked the MD5 sum of both the ISO file and the CD after it was burned, and they both checked out, so I don't know what is going on. :(

Here are my specs:

Gigabyte P35-DS3R Motherboard
Intel Q6600 G0 CPU
2x1GB G.Skill HZs, DDR2 800MHz
NVIDIA 8800GTX
etc...

I'm using the 64-bit ISO.

Any help would be greatly appreciated.  Thanks! :D

Have you tried selecting the reduced Graphics boot option? I believe this is option #3.
This usually works for me when option 1 fails.

---

