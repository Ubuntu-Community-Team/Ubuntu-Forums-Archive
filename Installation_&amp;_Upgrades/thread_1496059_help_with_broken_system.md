---
title: "help with broken system"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by roschell on 2010-05-28
hi guys,

I wont delay and go strait to the problem. 

How to rescue broken system 8.04. I do currently have on hand alternate cd of the system. 

The guide from ubuntu wiki does not seems to work as I receive always 'grub-install' not found. 

There is no windows on the laptop and only three (3) partitions. 

sda1 root
sda2 swap
sda3 home

Thanks for help
roschell

---

### Post by roschell on 2010-06-04
well, it seems to be finally fixed.

What I did was:

accept the 
>Rescue broken system link,

>get into the shell from the root partition, its really good idea to keep record of it or run a command to find it

when in the command line

>sudo apt-get update

>dpkg --configure -a

>sudo apt-get upgrade

and that was it!

perhaps there is better to run the sudo apt-get update again before the dpkg, nevertheless it worked well for me, even with the graphical issues during the whole process.

---

