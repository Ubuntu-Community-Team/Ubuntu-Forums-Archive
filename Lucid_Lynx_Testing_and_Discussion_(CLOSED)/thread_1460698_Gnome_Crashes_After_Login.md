---
title: "Gnome Crashes After Login"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nzv8fan on 2010-04-23
I am running Kernel 2.6.32-21-generic and have all the updates to Ubuntu 10.04 as provided through the update manager, in addition to this I am running Radeon HD with OpenGL renderer string: Mesa DRI R600 (RV620 95C4) 20090101  TCL DRI2

Something in the updates today has broken my ability to boot and login to Ubuntu. 

When my system boots it presents me with a blank screen, then a flash of the purple Ubuntu boot screen for 1 second. The login screen then shows, I select my username type my password and press enter. The login dialog box then disappears and the welcome music is played. At this point I am left with the purple background of the login page - my desktop background does not load, and neither does the menu bar at the top of the screen or the task bar at the bottom. Pressing ctrl-alt-f1 or any of the other f keys does not load and causes my mouse to vanish. At this point I can only hard power off my system. 

I have managed to boot successfully into Ubuntu using Gnome Failsafe. 

My system is an Asus Laptop, tri booting, Ubuntu 10.04 x64, Ubuntu 9.04 x64, Windows Vista. Intel Core 2 Duo Processor, 4GB Ram, Radoen HD 3470 graphics card. 

Where do I start to figure out what has broken?

---

### Post by dino99 on 2010-04-23
have you check system --> admin --> hardware driver to see if your driver is activated ? 

[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

---

### Post by nzv8fan on 2010-04-23
Of course that was the first thing I checked, I stated that in my post

> **nzv8fan said:**
> I am running **Radeon HD** with OpenGL renderer string: Mesa DRI R600 (RV620 95C4) 20090101  TCL DRI2


I am not running FGLRX.

---

### Post by Killigrew on 2010-04-23
Hi

are you using the xorg-edgers ppa? 
I have the same problem since this morning
i am using the r300g Gallium 3D Driver at the moment but it doesn't work
properly as well.

greetings

---

### Post by nzv8fan on 2010-04-23
Yeah I think I am, had to compile the Radoen HD Drivers from source back in Beta 1. I will check in the morning, it is getting very late into the night in Sydney.

---

### Post by theanswriz42 on 2010-04-23
Same thing happens on the girlfriend's laptop. Go to login to gnome, enter password, and then an error shows up on the upper right hand side of the screen complaining about a gnome power manager problem. I can get a better report of the exact error when I get home tonight.

---

### Post by Russ.Dill@gmail.com on 2010-04-23
A "me too" from me. R500+xorg-edgers  It seems that radeon.modeset=0 is a workaround.

---

### Post by theanswriz42 on 2010-04-23
> **Russ.Dill@gmail.com said:**
> A "me too" from me. R500+xorg-edgers  It seems that radeon.modeset=0 is a workaround.

Have you seen much video degradation with it?

---

### Post by Russ.Dill@gmail.com on 2010-04-23
Turning off kernel mode setting won't effect normal X usage or appearance. Text consoles are of course of less quality and it takes more time to VT switch.

---

### Post by nzv8fan on 2010-04-23
How and where do you set radeon.modeset=0?

---

### Post by Russ.Dill@gmail.com on 2010-04-23
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) is a good reference

---

