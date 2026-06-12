---
title: "(Gutsy) Black screen on startup"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by accountabilibuddy on 2008-01-30
I'm trying to move to Ubuntu from Windows Vista *shudder*; the only problem is, when I try to start it up... all I get is a black screen. :roll:

The CD worked fine and the installation went okay; I booted it up and went through a couple of hundred updates... so it *could* have been the updates that broke it. But... after that, the computer asked me if I wanted to use the drivers for my ATI graphics card...

Okay, so *maybe* it was a mistake to say yes without checking if I should. I just thought: "Hey, what's the worst that can happen?"... which I now realize is often followed by "Oh. *Oh.* Yeah, this is pretty bad. Probably shouldn't have done that." 8-[ Anyway...

I restarted for everything to take effect... and now all I get when I start up Linux (after the Ubuntu logo and the loading bar) is a black screen; and while it *is* a nice change to have something go wrong with my PC and know it's *my *fault, the black screen thing still kinda sucks. I've (tentatively) tried a couple of things to make sure the driver's loaded correctly (like "apt-get install xorg-driver-fglrx"), and it seems fine; I've also checked the installation CD for flaws, and it's also fine. Any-one know what I can do?

My PC specs:
Processor :	AMD Athlon 64 X2 4200+ @ 2200 MHz
Physical Memory :	2048 MB (2 x 1024 DDR2-SDRAM )
Video Card :	ATI Technologies Inc Radeon X1300 Series
Manufacturer :	Dell Dimension DIME521
Mainboard :	Dell Inc 0CT103
Chipset :	nVidia nForce 410


Err... also... I'm a newbie to the whole Linux thing, so you might have to dumb down your instruction a little.8-[ Sorry.

---

### Post by PmDematagoda on 2008-01-30
Boot Ubuntu in Recovery Mode and execute:-
```
dpkg-reconfigure -phigh xserver-xorg
```

After the X-Server has been set to defaults reboot the system using:-
```
reboot
```

Note:- Booting Ubuntu in Recovery Mode means that you are immediately brought to a Command Line Interface or terminal.

---

### Post by accountabilibuddy on 2008-01-30
Thanks! :D Problem solved.

---

