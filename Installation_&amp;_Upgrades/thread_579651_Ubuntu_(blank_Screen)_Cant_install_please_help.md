---
title: "Ubuntu (blank Screen) Cant install please help"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by shadycuz on 2007-10-18
Hey guys,

This is my story. I used Ubuntu fawn for a while. One day it just stopped booting. So I tried to re-install but I kept getting a blank screen. So i gave up and decided to wait for Gutsy. 

Well now it's here. And it won't install either. 

I'm just confused because I never had a problem booting from a live cd. And now it wont. I haven't changed any hardware setting or anything.

So I have tried x64, x86 , feisty or gutsy, alternate or live cd's. 

What happenes with the live cd's is that after i hit install the loading linux kernel box pops up on the screen but after it loads the monitor powers off. The green text that should run in the back ground never does. 

With the alternate cd's the loading Linux kernel box pops up and the green text behind it runs and the install goes great. But after rebooting to run for the first time, the monitor litteraly powers off. 

I have ran Ubuntu many times before on this same machine same monitor and same hardware.

If any one knows the solution please help me.

---

### Post by ebichete on 2007-10-18
Try adding "nosplash" to your GRUB boot line. If that works around the bug, then file a bug report in launchpad agaiinst "usplash" and give your hardware (esp. monitor and graphics card) details.

---

### Post by shadycuz on 2007-10-18
How do I do that?

---

