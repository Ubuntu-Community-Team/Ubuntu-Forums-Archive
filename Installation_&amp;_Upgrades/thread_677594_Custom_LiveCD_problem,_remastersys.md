---
title: "Custom LiveCD problem, remastersys"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by FmC on 2008-01-25
Im trying to make my own custom Ubuntu LiveCD, centered around music composing and recording/production.I want to have everything set up and ready to go so I can just pop the live CD/DVD into any computer, plug in my sound card and mixer, and get to rocking out. This includes themes/wallpapers, menu setups, programs, and drivers for my audigy sound card. 

Anyways, to the problem. I used remastersys to compile a backup iso, (sudo remastersys backup) When I put the DVD in, get to the Ubuntu install menu, and select "Start/Install Ubuntu", it ends up with this error dialog:

[IMG]http://img210.imageshack.us/img210/4607/errorzw1.jpg[/IMG]

--
One thing I noticed is that it shows the Ubuntu Studio loading screen instead of the generic Ubuntu loader. This could very well be the problem, because the xserver doesn't work right on my original box when I boot from the Ubuntu Studio boot option(if that makes sense)

---

### Post by FmC on 2008-01-25
Ok, I've made some progress. The reason it's doing this is because it's trying to load the 2.6.22-14-rt kernel(the ubuntu studio kernel), instead of the working kernel, the 2.6.22-14-generic one. 

I deleted the rt kernel from my /lib/ directory and recompiled/reburned the ISO and..

NOTHING! Well, not nothing, but still the same error as before. It's still trying to load the RT kernel rather than the generic one, and giving me the same error message.

gah

---

### Post by TJCIB on 2008-01-28
I'm having the same problem.

I loaded an original LiveCD (downloaded from ubuntu site) on one computer, everything was great.  I moved on to the next computer and I got the studio load screen.  I tried loading it from there, and I got it loaded and right as I thought I had it, the system restarted.  It continues to restart and I can never get the entire OS loaded before it reboots.

So I moved the HD to another computer and installed ubuntu on that system like normal (normal boot loader and everything).

A motherboard issue maybe?

I know you're trying to run in LiveCD mode, but thought I would share my similar experience with installing...

---

