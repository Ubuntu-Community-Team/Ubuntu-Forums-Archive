---
title: "X58 needs nolapic to boot 10.04 x64"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by TiberiusT on 2011-05-21
Stuck!

Foxconn Bloodrage GTI i7 920 6GB RAM. BIOS at defaults. 10.04 x64 with Kernel 2.6.32-28

I've formerly run Maverick x32 wout issues, but now I've gone back to 10.04LTS bcos that's what the other PCs in the house are using very happily. Boot is on separate drive to Win7 which is on a RAID0 and has functioned perfecto at 4.00Ghz for over a year with various BIOSes. BUT 10.04 x64 will only boot with nolapic in the command line. hpet=verbose makes no difference, both attempts hang at Checking Battery State which I understand is a kind of generic place to stop for a multitude of problems. I change HDD Boot priority in BIOS manually to boot the two OS'es. nolapic boots fine but of course uses one thread only and is ... glacial.

I have tried several different BIOSes P4,6,7,9,11, G40 and G42. All at defaults.Same issue.

I have not yet tried another Ubuntu bcos I am new to Ubuntu and I want to standardize and learn one version to start with so I can improve the setups on all PCs. I have read about the X58 apic issue but hpet=verbose seems to solve it for a lot of people. Also, I've seen others suggesting to 'update the kernel' to 36 or higher. Is that a good idea? Will that break full 10.04 program compatibility with the the other PCs? What's the best way to go about this?

Tks in advance to anyone. I can of course give further details if required, but this seems to be a known issue and maybe someone just knows the best way to sort it.

T

---

### Post by mörgæs on 2011-05-23
If you know that 10.10 works well, I guess the obvious solution is just using this (in a fresh install). 

You will not encounter problems sharing files with 10.04, in fact there is not much difference between 10.04 and 10.10 except for a number of bug fixes.

If you have more computers in the house, my advice in general is running different releases (or maybe Xubuntu on one). This gives a good opportunity of learning and comparing.

---

### Post by TiberiusT on 2011-05-24
@Morgaes
Much obliged for your time...tks. I had another go at it last night - messing around with the HPET settings in various BIOSs and apic this and nolapic that etc etc in boot options. Certain combos seemed to boot but always one thread only. I am only hip shooting the issue though - no real idea what it all means.

I'm kinda proud that now on my 5th install I have managed to solve every problem that every piece of often dodgy hardware has thrown at me - always on 10.04. However, googling 'hpet' takes me into yet another undiscovered country and I'm all learned out for the moment. 10.10 it's gonna be then....I'm not seeing too many positive comments abt Natty around here. 

T

---

### Post by TiberiusT on 2011-05-25
I won't mark this as [SOLVED] ...because it wasn't properly. Anyhow, I installed 10.10 x64 wout any problems. As the boot flashes up the screen I notice a very different approach by this version to apic and multithreading generally - it seems to perform a very different and more thorough checking routine than 10.04 and most importantly, it works wout any tweaking.

All fine now.

T

---

### Post by TiberiusT on 2011-11-03
Well, after several months of part-time messing about (I mainly use Win7 on this PC) I have finally come to the conclusion that this mobo does not support Linux. How did I get there?

Maverick ran OK, but nowhere near perfectly, and I had issues when I started doing some real computing on it. My n00bness assumed that it was just Linux being Linux. However, I now have 6 machines smoothly running (X)Ubuntu, mostly Oneiric or Natty nowadays and my newfound experience told me that something wasn't right with this rig.  At all. 

Basically:
- Installing any distro has always been a complete pain - often upto 5 efforts 
- my current install (Oneiric x64, various BIOSes at defaults) was throwing various random headfits (losing network, screen rendering errors, wouldn't shut down, took about 3 minutes to boot). Looking thru the logs revealed a metric crap tonne of errors - often to do with ACPI and doing a boot into recovery mode it 'sometimes' reported stuck CPUs, but sometimes not, amongst a multitude of what appeared to be very serious issues.
- Foxconn do not certify the board to run with Linux and other Foxconn boards have severe Linux issues. See here among others: [http://ubuntuforums.org/showthread.php?t=868377](http://ubuntuforums.org/showthread.php?t=868377)

I didn't know there was such an issue with some boards do/some boards don't. Another tick in the learning book for me then and I'll always check for Linux certification when buying Mobos from now on.

T

---

### Post by TiberiusT on 2013-01-06
[COLOR=#000000][FONT=Calibri]I  think it's always nice to keep threads updated - especially if the  issue is solved. And it is, bcos Xubuntu 12.10 x64 works - perfectly -  for 3 weeks of use now.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]I  gave up running Linux on this PC and left it as a Win7 box doing video  encoding only. But the other day I accidentally booted a USB stick with  12.10 on it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]I  had meanwhile updated the Bloodrage BIOS to G44. Maybe it was that,  maybe it was a Linux kernel change generic to X58s, maybe team Ubuntu have done something clever. Whatever, it  works...and boy does XFCE fly on it with an SSD - it's like every menu  press has appeared b4 your finger has even released the mouse button,  and you'll never overrun it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]Splendid [/FONT][/COLOR][IMG]https://lh6.googleusercontent.com/dxlYQMiBeSVeLtSxdsZTNw3XHMZgRSzvkiAGr7Cgfuxa1WhaslvpkypwFERr4vt37w-h0R-Bb-KA-Bsw_GuuKxPvwb1l0AUgN_QZarIfMKxXnOlb5yZA[/IMG][COLOR=#000000][FONT=Calibri] Ubuntu GNU/Linux is really starting to kick some compatible butt. Thanks[/FONT][/COLOR].

[COLOR=#000000][FONT=Calibri]T                                        [/FONT][/COLOR]

---

