---
title: "Ubuntu not booting."
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by GerhardVic on 2010-07-31
Hey,

First off, I'm a new Ubuntu user, I've had no experience with Ubuntu or any other Linux distro what-so-ever - and I'm using Ubuntu v10.04 (Desktop).

My Computer is a Dell Studio 15 (v1557), with:
[list]* Intel i7 720QM (@1.6GHz)
* 4GB 1333MHz DDR3 SDRAM
* 512MB ATI Mobility Radeon HD 4570
* 500GB 7200RPM SATA HDD[/list]

It used to have Win7 on it, though prior to installing Ubuntu I nuked the HDD, using Darik's Boot And Nuke.

The issue I'm having is that around 80% of the time that I boot the laptop, after loading the BIOS it will not boot Ubuntu at all. Instead, it will sit on a black screen which looks exactly the same as [THIS (click)](http://1.bp.blogspot.com/_Rs53-MPsJaI/SrHXyb0Q01I/AAAAAAAAOU8/x3x89sVMOuk/s400/Win3x_Black_Screen_of_Death.gif).

I've tried reinstalling Ubuntu off my USB multiple times to no avail. 

As a note, if I hold L-shift I can enter the GRUB menu, selecting selecting Ubuntu or recovery mode both do NOT work for the vast majority of the time.

Any help with getting this working would be highly appreciated :).

---

### Post by oldfred on 2010-07-31
Your black screen link is very helpful.:)

Since you seem to boot some of the time, have you checked the log files which will also have the previous boot in them to see if something is out of place. A long time or repeated tries at loading a driver or some other issue.

System, Admisintrations, Log File Viewer. 
Check messages & kernel first, they will be long.  Boot log is not enabled so it is empty. I check them all if I have issues.

---

### Post by GerhardVic on 2010-07-31
Hey, thanks for the response.

> **oldfred said:**
> Your black screen link is very helpful.:)

Hehe, I couldn't think of any other way to describe it, aside from "Black screen with flashy line thing up in the top left.".

Anyway, I hadn't check the logs, mainly since I had no idea where to start.

Though interestingly, I was using the 32bit version of Ubuntu, on a whim I decided to try the 64bit version (removing the 32 bit version in the process), and the issue has basically resolved itself, it boots 100% of the time now with no issues what-so-ever.

Since I don't plan on using my laptop for anything overly unusual - all I need is Dropbox (which has a 64 bit version), an internet browser and a word processor - I'll probably just stick to the 64 bit version.

---

