---
title: "borked linux with jaunty kernel and Xserver, opengl glitch + cant logoonto gnome"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by seish on 2009-02-03
Hey computer owners, 

Here's how I messed up my system.
I wanted to compile a 2.6.28 kernel cuz I was with 2.6.27.


When I compiled my previous kernel I followed
[http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt+cpu](http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt+cpu)
 to compile the acpi-cpufreq.ko module to undervolt my cpu.

But the thread is outdated, and the website for undervolting is down, all I found is a random post on the thread with a 2.6.28-4(x64) precompiled module for jaunty. 

It didn't work on my custom 2.6.28 kernel(compiled it following master kernel thread in howtos) so i thought it was an old version(no 28-4 in kernel.org just 28 ) so I added the jaunty repos and installed the 2.6.28-4. I installed the new X too. Turned out it wasn't me but the cpufreq module was bogus cuz it didnt work again. 

But after upgrade i have this:

> My hardware acceleration randomly starts glitching(kwin, compiz, etc...need reboot to fix it), it ok 1 sec then idles 1 sec. my warcraft 3 is streched out of my screen and also glithes 4/5 times I try to start it. 

>GDM and gnome fail to load, I think some missing libraries from an accidentaly upgraded package.

My xorg.conf is default , except i added "accellmethod" "EXA", but the glitch persists even if I comment it out.

Should I remove jaunty repos and downgrade back, will it fix my bugs( you need to help me do that)? 
also, do I need the new Xserver to use the 2.6.28 intel graphics?

---

