---
title: "kernel .13 problems"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-10-11
I just updated karmic and got the new .13 kernel. Upon bootup the system hung on a black screen after the white ubuntu logo passed. I mean, it's completely black, no way to input anything. Any ideas? I'm posting this using the previous kernel.

---

### Post by Claus7 on 2009-10-11
Hello,

exactly same problem here!

Regards!

---

### Post by rex4u on 2009-10-11
> **oboedad55 said:**
> I just updated karmic and got the new .13 kernel. Upon bootup the system hung on a black screen after the white ubuntu logo passed. I mean, it's completely black, no way to input anything. Any ideas? I'm posting this using the previous kernel.

Any progress in Recovery mode...?

---

### Post by Longinus00 on 2009-10-11
What graphics card are you running?

---

### Post by simmeson on 2009-10-11
Can confirm this too, I'm writing this from .12 kernel.

---

### Post by Tux Aubrey on 2009-10-11
The .13 kernel certainly won't boot karmic in VirtualBox for me.

---

### Post by DougieFresh4U on 2009-10-11
Is your grub menu ok?

---

### Post by ppjose on 2009-10-11
same problem here!! 

I have a nvidia 6600GT

---

### Post by Claus7 on 2009-10-11
Hello,

this is how I solved the problem in my ubu box:

I entered the recovery mode of the new kernel in question:
2.6.31-13-generic

there I chose the system to start at command line mode as root. Then I typed:
```
startx
```
and the result was (among others):
> (EE) NVIDIA (0): Failed to load the Nvidia kernel module!
(EE) NVIDIA (0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error: no screens found

Please also check the log file at "/var/log/Xorg.0.log" for additional information

So I had the file for the Nvidia drivers in my home directory and as root I installed this kind of driver. The next time I booted everything was ok.

Regards!

---

### Post by dino99 on 2009-10-11
work fine here with 8500 gt, last kernel 13.43

---

### Post by darco on 2009-10-11
A couple of times, I would get the black screen. Would have to hard boot, then go into the previous kernel,the system would say I need to run fsck manually. Then I would do a sudo reboot,and the new kernel boots fine.

darco

---

### Post by JohnJackson on 2009-10-11
Strange, I get this problem trying to load the daily live CD from 11/10/09. However I don't get this problem on another computer with the latest updates.

---

### Post by Riot@ct on 2009-10-11
> **JohnJackson said:**
> Strange, I get this problem trying to load the daily live CD from 11/10/09. However I don't get this problem on another computer with the latest updates.
I have the same problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/448142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/448142)

giuseppe

---

### Post by Riot@ct on 2009-10-13
With today daily build (13 Oct. 2009) the problem persists.

---

### Post by lovinglinux on 2009-10-13
If you have nvidia 180 driver installed, try to remove it and install version 173. This solved this issue of Ubuntu hanging before the gdm.

Unfortunately, I don't know how to do that from the recovery console, so I had to re-install. In fact I have installed several times until I realized it was a nvidia driver problem :)

Bug report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/421442](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/421442)

---

### Post by joey-elijah on 2009-10-13
> **dino99 said:**
> work fine here with 8500 gt, last kernel 13.43

OMG! Finally someone has the same GFX Card as me...


...sorry, as you all were...

---

### Post by sports fan Matt on 2009-10-13
Anyone have issues with intel? That is my card and im considering waiting it out for a few hours

---

### Post by sports fan Matt on 2009-10-13
just reporting no issues here with .13 kernel.

---

### Post by lovinglinux on 2009-10-14
This bug has been fixed with the latest updates! =D>

---

