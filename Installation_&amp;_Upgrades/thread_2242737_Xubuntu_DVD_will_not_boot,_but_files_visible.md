---
title: "Xubuntu DVD will not boot, but files visible"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by john_ladasky on 2014-09-03
Hello everyone,

I have an older laptop (IBM ThinkPad Z60m) on which I have been running Ubuntu 12.04.  I find myself needing more recent versions of Python, Scipy, and Matplotlib than are provided in the 12.04 repositories.  I have managed to bungle the manual upgrades of these packages (chasing down package dependencies by hand is never easy, even when I succeed).

To solve the dependency problem, I am trying to do what I always finds works, which is to upgrade Ubuntu.  I want to upgrade to 14.04.1.  When I attempt to install 14.04.1 from the Update Manager, I get a warning message saying that the Unity3D desktop might be too heavyweight for my system.  The folks on the Matplotlib mailing list agree (but I think that 12.04 has Unity too?), and recommended that I try Xubuntu instead.

My laptop can read DVD's, but not burn them.  I burned the Xbuntu 14.04.1 i386 ISO to a DVD on another system.  When I insert that DVD into my laptop, it seems to try to read the DVD, however it does not boot from the DVD.  I have confirmed that the first device in my BIOS boot sequence is the optical drive.  Once I have booted into 12.04, I can browse the DVD with Nautilus, no problem.  But without booting from that DVD, it doesn't look like I can try/install Xubuntu 14.04.

I'm mystified.  Any hints are appreciated.  Thanks!

---

### Post by yancek on 2014-09-03
Might have been a bad download.  Did you do an md5checksum on the iso before burning it as an image to the DVD?  Do you have another computer available you can use to try to just boot the DVD to eliminate that possibility?

---

