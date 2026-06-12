---
title: "Installing multiple ide drives"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by Squish on 2007-06-17
ARGh, in frustration


Huh...
Ok
I am installing ubuntuCE<christian edition> Feisty<7.04> on 2 computers.

First computer:
Master - 6 gb
Slave - 6 gb

The master has ubuntu 6.10 already installed on it, and I have upgraded the computer by putting a new 6 gb slave harddrive in it. However, I cannot for the love of god, figure out how to get this to work with ubuntu. WHAT ON EARTH DO I DO TO GET IT TO BE STORAGE FOR THIS COMPUTER.
I can detect it, and it is installed properly, and it gets detected by gparted, however I do not know what to format it as, nor can I figure out how to mount it?!?

Second computer
So I built this computer from a ton of differant parts, and I have ended up with this:
Primary master - 10 gb
Primary slave - 10 gb
Secondary master - DVD rom
Secondary slave - 3 gb

I have tried to install feisty, which I couldnt - some stupid live cd error that takes too long to work around, - and now I am trying 6.10 however, I do not know how to install multiple ide drives.
My first solution was to partition the primary master as "/", the secondary master as "/home", and the secondary slave as "swap"
However, when I boot, I get "error 22"
Arghhh
There must be an easier way!
I am all for the easy install of ubuntu, because it is, however, with multiple drives, including raid arrays, it is a pain in the ***, lets hope the next release at least supports raid!

I need a response asap, because the people I am doing this for are threatening to install windows 98 *Shivers* because it is easier....
PLEASE HELP!

---

### Post by bulldog on 2007-06-17
I have not much time at this moment,but I will try to put you on the right track.

Problem one.
Format the second hdd ext3 and make a mountpoint in /media called whatever you want.
Edit the fstab with the information needed for this device,you can find all you have to know on this site:
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) 
Look under beyond the basics

The second error probably has to do with your hdd configuration.
Ubuntu has an other way to name devices as the BIOS does.
So if you think you're dealing with the master hdd,which is called hd0 under ubuntu,it's a fair change you're messing with hd1.
So in order to get this things to work,you have to know how the devices are numbered on ubuntu.
The best thing I can offer for now,is the advice to download the gpartred live cd.
It's a small download,55MB,burn this to a cd and boot from it
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
This tool gives you a graphical partitioner which is much easier to use.
Make your partitions as you like them,  / = ext3 , /home = ext3 and swap = swap file system.
After done,don't forget to apply your changes otherwise nothing is happening,and exit gparted.
Boot the ubuntu cd,if you have time enough,I would recommend the 'alternate cd' which is a text base installer which will do the job much quicker,and mount the partitions you've created and it should work.

Be back later this afternoon,to see how things are going.
Good Luck:D

---

### Post by Squish on 2007-06-17
Problem 1 - SOLVED

Thank you so much for the site.
My plan now is to use the solution from number 1 to fix the other.

QUESTION?!?

This ubuntu is a special version, known as ubuntuCE <christian edition>
If I do the update command<because the version of ubuntuCE I am running is 6.10, and I want its 7.04>
$ gksu "update-manager -c"
Will it update it to regular ubuntu, or the 7.04 version of ubuntuCE???

---

### Post by mrphantastic on 2007-06-17
Hey, Squish you need to go to the update manager prog on your current Ubuntu CE and update it to regular Ubuntu 7.04, if you can...i don't know what the update procedure will do.  But, that doesn't matter, because...there is a sweet program on the Ubuntu CE website that converts Ubuntu 7.04 to the newest overlay of Ubuntu CE (i think it's like Ubuntu CE 3.2 or sumthin, could be wrong tho)  Essentially, CE is a layer or app addition over or with regular ubuntu...think of it as just an expansion pack for a videogame..., the conversion anyway...

---

