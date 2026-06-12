---
title: "ASUS F1A 55-M LE 12.04 installer crashes"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Peter09 on 2012-05-01
Yesterday my Son bought a new machine to me so that I could assist in installing 12.04. The machine has no O/S installed and is a basic ASUS F1A 55-M LE motherboard, nothing else installed except 4GB of memory.
 
We tried to install 12.04 (64 bit) using flash drives and also a CD. 
 
Initially we could get nothing but a blank screen, but using 'nomodeset' in the grub command line allowed the Live CD to run OK.
 
Trying to install resulted in an installer crash - every time :( about 3/4 of the way through (during a section talking about transferring settings).
 
This also occurred on the Alternate text based installer.
 
Can anyone suggest any options here?

---

### Post by lJ9%3MR&gt;sa on 2012-05-01
I'm having similar problems on an older computer I have with only 1gb of ram. The installer of any Lubuntu, Xubuntu, etc... Will crash at 50% and go to live desktop. I think it has to do with AMD CPUs or something. I hope they release a fix.:p

---

### Post by Peter09 on 2012-05-08
Well, over the weekend I tried installing 11.10, with an aim to upgrade to 12.04. 
 
LiveCD ran OK, (needed the boot option of 'nomodeset'), and gave me a working desktop - great. The install also went OK, no issues or crashes. Looking Good.
 
On trying to boot the installed system, :(, failure. Something to do with the on-board radion graphics, the system stalls at UserSplash (or at checking battery......)
 
Its a bit annoying that the LiveCD works but the install does not. Currently, despite trawling the internet - no resolution.

---

### Post by haresear on 2012-05-08
I assume you tried using the "nomodeset" boot option when trying to boot the installed system? It sure sounds like a video driver problem.

---

### Post by Peter09 on 2012-05-08
Yes, tried

>  
[LIST]
[*]nomodeset,
[*]acpi=off
[*]xforcevesa
[/LIST]
 
at some point in the precedings, plus combinations of all.

---

### Post by haresear on 2012-05-08
Is recovery mode available in the grub boot menu, and have you tried that?

---

### Post by Peter09 on 2012-05-08
Yes, 
can get to the root prompt (without the network) - thats because its a wireless connection. Could go hardwired if needed.
 
Doing:-
 
```
 
lspci -C video

```
 
shows the video card as 'unclaimed'

---

### Post by haresear on 2012-05-08
Sounds like it isn't loading the correct graphics driver. I haven't dealt with an ATI graphics problem for quite a long time, so I'm not that familiar with recent drivers. The last ATI card I had used the driver module 'radeon' -- not sure if that is still relevant. If you boot with the live CD again and use 'lsmod' in a terminal, you might get a clue for a graphics driver module that will work. If you can figure out what driver module you need, you might be able to force it to load with a boot parameter. Years ago I was able to load a particular graphics driver with the boot parameter 'xmodule=xxxxx'. Not sure if this parameter still works or not. Sorry I can't be more help -- maybe someone more knowledgeable will chime in soon.

---

### Post by Peter09 on 2012-05-08
Thanks I'll try it when  I get home.

---

### Post by Peter09 on 2012-05-09
Solved it:
 
yesterday when I booted the system it came up to the command prompt WITH NETWORKING, this allowed me to try
 
```
 
sudo apt-get install fglrx

```
 
that installed a large number of additional items. Next boot it worked, no problem. I then upgraded to 12.04 and - yes its there. 
 
Obviously for some reason the installer does not recognise that there is a Radeon card onboard.
 
Thanks to everyone for help and assistance.

---

### Post by haresear on 2012-05-09
Great. Glad to hear you got it sorted out.

---

