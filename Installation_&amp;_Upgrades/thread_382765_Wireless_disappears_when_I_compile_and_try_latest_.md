---
title: "Wireless disappears when I compile and try latest kernel 2.6.20"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by maril on 2007-03-12
Wireless disappears when I compile and try linux kernel 2.6.20

It is still listed in the device manager, but I no longer see it in the network administration window, just Wired and Modem are listed.

Running 6.10

2.6.17 current kernel, downloaded source for 2.6.20, copied config (uname something), make menuconfig, dpkg something...  figured it would all be the same since I copied current config.

I'm hoping that it is something in the kernel config file that I need to tell it to install.

:: please move me if I'm in the wrong forum section ::

---

### Post by hardyn on 2007-03-12
what wireless card are you using?

you must copy the firmware from the orignal kernel libs, to the new one.
I have had to do this once, and i would have refresh myself on how to do it, but this should be enough to get you searching this forum in the correct direction...

if you have no joy in a couple of hours, i will figure it out again, and get back to you.
cheers.

---

### Post by maril on 2007-03-12
really?  so I intalled Ubuntu and it automagically installed, then if I recompile the kernel I have to copy a wireless library?  I will look for how to find that

---

### Post by hardyn on 2007-03-12
>  hardyn, the i2915 will work if you recompile the kernel as long as you copy the firmware in a new dir with the name given by 'uname -r' in the /lib/firmware dir.


this was what was explained to me when i had the same question.
hope this helps

---

