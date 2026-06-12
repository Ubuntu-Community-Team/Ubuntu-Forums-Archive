---
title: "problems with partition in HP dv6000us"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by gakna on 2007-08-18
Hi, i am trying to install Ubuntu in my laptop HP Pavillion dv6345us. The thing is that when i start the installation from the LiveCD the option to partition the disk doesn´t show up as it did when i installed it on the desktop computer. What is your suggestion? i am completely new to all this so i will really appreciate details! Thanks ;)

---

### Post by merlinus on 2007-08-18
What is on the laptop?  Is the drive already partitioned?

-merlin

---

### Post by gakna on 2007-08-18
No, it is not partitioned. The computer came with Vista installed and i want to install Ubuntu together with it. The thing is that i when i did it in my desktop, the installation program offered me to partition the disk as part of the installation process but it didn´t with this laptop. What could be wrong? and what shoul i do??

---

### Post by merlinus on 2007-08-18
Here's why:

If using vista, then use its disk manager to shrink its partition and make space to install ubuntu.

Beforehand, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back to original size after installing ubuntu), and defrag several times.

-merlin

---

### Post by gakna on 2007-08-18
Thanks for your help!! couple of questions though: how do you set virtual paging to zero?? and, once i do all this...when i run the liveCD it will recognize the partitions?? Thanks!!

I know i should open another post but maybe you know about this: in my desktop i am having problems with my graphic card ATI Radeon 9250 128mb and the 3D graphics (which many people is having but can´t make anything clear out of the posts). Apparently, for that model i have to use the free drivers and AIGLX in order to run the 3D acceleration to use Compiz Fusion, but i can´t make it work. If you know something about it it will be extremely helpful! THANKS

---

### Post by merlinus on 2007-08-18
I do not use vista, but believe virtual paging is somewhere in the System Tools menu.  You can search Help for it.

As for your video card  -- after install you can get to a gui via Recovery Mode from the opening menu and search for the drivers.

-merlin

---

