---
title: "Ubuntu 14.04 - update to kernel 4.4 caused KernelOops error"
date: 2017-11-13
forum: Installation &amp; Upgrades
---

### Post by rdbowers on 2017-11-13
I just put together a special computer  (Intel D2500CC motherboard, internal graphics (using 800x600 resolution), 4gb ram, 80GB hard drive) - designed for 12v operation (including a 7 inch touch screen display I cobbled together - 800x600 is the highest resolution it will display that is clear and easily read).  

I tried installing 16.04 on it, but it just wouldn't work (I couldn't even get to where I could diagnose the problem - 16.04 was installed on a flash drive and it just wouldn't get anywhere).  I went with 14.04 and it ran on the first install (a couple of minor bugs with settings and getting the small/lower resolution screen going, but that's it).

I did a 'standard' update (automatic) and it still ran fine, version 3.13.  Then I used Update Software, and the computer now crashes when I try to run the latest update (Kernel 4.4 - caused a KernelOops error).  I can get into Grub2 no problem, and if I choose one of the older kernels it runs fine (I got the KernelOops error showing up when I booted under 3.13 - reporting a problem with 4.4).  The latest Kernel (4.4) starts trying to boot, the screen goes purple for a bit, and then goes black with a "no signal" alarm on the display.  If I power down the computer, it shuts down immediately - indicating that the system had already shut down.  The hard drive light stops flashing, another indicator that the system shut down.  I 'allowed' the computer to submit a report of the problem (I've submitted a report a couple of times.)  It's consistent - I just cannot get the 4.4 Kernel to work.

This system is set up to run some specific equipment (a couple of SDR radios and interfacing) and I don't use it on the internet (although I do have a temporary USB WiFi adapter on it at present to get the files I need copied over).  I don't really need to put anything 'latest and greatest' on it because of my planned usage.  (1) Can anyone give me suggestions on getting 4.4 to work, or (2) eliminating the latest Kernel update so that I can continue with what does work?

Thanks!

Bob

---

### Post by mörgæs on 2017-11-14
Though you maybe don't need a newer kernel I would still recommend that you try it. 4.4 is old news and I don't expect anyone to be interested in bugs reported here.

How does the hardware work in a fresh install of X/Lubuntu 17.10?

---

### Post by rdbowers on 2017-11-14
I'm not familiar with X/Lubuntu 17.10, and stick with the LTS versions of "regular" Ubuntu (I'd even be going with old-style Gnome desktop, except that the Unity version works better for what I want to do).  

Funny thing about the version number, because 4.4 (not sure which subversion) was the most recent update my machine received - so it's not "Old News" here.

16.04 was dead before it left the gate here... I couldn't get to step one with it on this system and ended up putting 14.04 on.  Maybe installing 16.04 as an upgrade would work - but I don't want to have to spend hours trying to undo problems if it didn't work as planned.  I've already had to take a lot of time (without luck) trying to figure out why the latest version wouldn't work.

---

### Post by mörgæs on 2017-11-15
> **rdbowers said:**
> ... and stick with the LTS versions of "regular" Ubuntu...
What has 16.04 done to earn your trust? Sounds like it has only brought you problems. 

> **rdbowers said:**
> 
Funny thing about the version number, because 4.4 (not sure which subversion) was the most recent update my machine received - so it's not "Old News" here.

But it is to the developers. There is no point in reporting bugs for such old stuff since people are unlikely to pay attention. 

> **rdbowers said:**
> 
...trying to figure out why the latest version wouldn't work.
You still haven't tried the latest version which comes in 17.10. Better to do some open-minded testing before narrowing down the solution to only LTS and only Ubuntu.

---

### Post by rdbowers on 2017-11-15
Error 1 - I'm not running 16.04, but 14.04 (and the only version on that computer that doesn't work has a 4.4 Kernel).  I'd run 12.04 if I thought it would give me an advantage.  (I have a computer - in my shop - that runs dos, and don't consider anything obsolete if it meets the need.)

Error 2 - I have no interest in the latest and greatest, and I consider a computer (and OS) to be a tool.  I don't like to experiment - I have enough of that IRL (I'm a Doctoral Candidate and researcher - and laugh when people start implying that I need to learn something important to them rather than answering a straight-forward question).  (Once my research is finished and my dissertation written and defended, then this computer will get 16.04 - or 18.04 if it's available.)

Error 3 - I resent your comment about being open-minded.  You don't have the right to tell me how I should be. 

No, I'm not going to experiment with 17.10 - and that's final.  I need help with 14.04 (or ideas how to get 16.04 to install and run), and if you aren't willing to provide that help, maybe someone else will.

---

### Post by rdbowers on 2017-11-15
Problem solved, although I'm not too sure what the problem was (possibly something like an added space - a typo).  I re-edited the /etc/default/grub file and updated grub, and now the monster is up and running with the most recent kernel version.  Funny how the older kernels worked but 4.4 wouldn't.

I still don't know what's wrong with 16.04, but it may be related to the problem with 14.04 - although there is no screen connected to the LVDS connector, it seems that Ubuntu is still 'finding' a screen and although supposedly disabled in BIOS, considered it enabled and active.

---

