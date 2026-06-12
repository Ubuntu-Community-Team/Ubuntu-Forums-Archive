---
title: "Can't boot default kernel after upgrading from 9.xx to 10.04 lucid lynx"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by euux on 2010-07-21
hi, 

after upgrading to lucid lynx ubuntu doesn't boot with the new kernels 2.6.32-22-generic and 2.6.32-23-generic (also in recovery mode). But it's does boot with the previous 2.6.31-21-generic kernel. 

At the time i was hoping to wait it out, but a new kernel has come and the problem persisted. I've been trying to find a solution for this but somehow, amid lots of failed boot blank black screen threads, i didn't relate to any solution.

The boot seems to go well until a pixelated logo appears (before the login screen), then goes to a blank black screen and there it stays stuck with no remedy.  

Looking into dmesg logs - albeit some differences between 2.6.31-21 and the newer 2.6.32-23 - the failed boot seems proper in both logs.

In Xorg logs the differences are bigger but i cannot pinpoint a source for this problem. 

Can anyone help me with this? 


PS:I've attached dmesg and Xorg logs.

---

### Post by rienesl on 2010-07-24
Nice! It seems, that a lot of people got that problem (including me) and after over a month, there is still no solution. How can that be?

---

### Post by euux on 2010-07-31
After all the search turns out that there is a official troubleshooting page about a set of issues related to lucid lynx, 2.6.32-* kernel and Intel graphics drivers: **[X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")**. (my machine has an 855gm graphics card.)

Because I already had lucid installed; and because the latest kernel is bootable with failsafe in recovery mode; I've applied the _Potential Solution: PPA packages_. I was expecting something different but now as far as I can tell those commands point the update manager to update a few packages related to Intel 8xx drivers, those updates will only be applied after rebooting and after running the update manager (in my case I've rebooted and the auto-update icon fortuitously appeared in the task bar). After authorizing the update and after rebooting, lucid lynx booted in normal mode with the latest kernel (2.6.32-24). \\:D/

This is solved for me. Good luck to you rienesl !

---

