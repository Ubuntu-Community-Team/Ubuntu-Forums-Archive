---
title: "Cosole option for Alternate CDs"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by charlie. on 2007-04-03
I never use the Ubuntu Live CDs. I find it much faster to install from the Alternate CDs because I don't have to wait for the slow live CD environment to load. Also, I prefer the text-based installer to the graphical one.

It is a little known fact that you CAN get a console on the alternate CDs. All you have to do is start the install process, hit Alt+F2 to change to another terminal and hit enter to activate it. This gives you a BusyBox terminal. I've just used this environment to stuff Grub back into the MBR of my HDD. (I chroot'ed into my real Ubuntu environment and proceeded as normal.)

While doing this, I though it would be cool if a menu option was added which sent you directly to a BusyBox terminal. (It could be called "Recovery Console" or something.)

I'm sure it's not a critically complicated change I'm asking for.

---

### Post by az on 2007-04-03
> **charlie. said:**
> I never use the Ubuntu Live CDs. I find it much faster to install from the Alternate CDs because I don't have to wait for the slow live CD environment to load. Also, I prefer the text-based installer to the graphical one..

It takes much longer to install from the alternate cd.

On a computer with 256 megs of ram, the live cd will take about four minutes to boot.  Once you click on the install incon and answer all the questions, the system will be rebooted into the ready-to-use system in about twenty minutes or so.

In contrast, the alternate cd takes about a minute to boot and the install (on a box with 265 megs of ram) will take just under one hour.  It takes longer to install from the alternate cd because it installs and configures each package individually.


> **charlie. said:**
> 
It is a little known fact that you CAN get a console on the alternate CDs. All you have to do is start the install process, hit Alt+F2 to change to another terminal and hit enter to activate it. This gives you a BusyBox terminal. I've just used this environment to stuff Grub back into the MBR of my HDD. (I chroot'ed into my real Ubuntu environment and proceeded as normal.)

While doing this, I though it would be cool if a menu option was added which sent you directly to a BusyBox terminal. (It could be called "Recovery Console" or something.)

I'm sure it's not a critically complicated change I'm asking for.

Isn't there already an option to chroot into a filesystem on the disk?  Is it called rescue mode or recovery mode?  It basically does what you describe, and as the final step, it offers you the choice of partitions which it has detected for you to chroot into.

---

