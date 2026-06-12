---
title: "Installation problem of 10.10, and the syslog &amp; partman files"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by dehiker on 2010-11-19
While trying to install ubuntu 10.10 on my laptop with newly burnt CD by myself, I got some problems.:(
As the installation came to "configuring apt...", it prompted that an error occur, and asked to upload /var/log/syslog and /var/log/partman files to somewhere.
 
I'm quite new to Linux, and cannot get any hint from the error prompt. Any ideas? Or anybody knows where I can get the help?
 
Thank you so much!
dehiker

---

### Post by oldfred on 2010-11-20
I am assuming that the install crashed and it wanted to upload (or automatically upload) the error logs for review. 

I glanced at logs and do not know enough to help. It looked like the installer was having issues reading sda1.

Were you just installing Ubuntu to the entire hard drive? Is this an older system? What are its specs? I saw something about limiting IDE transfer due to 40 wire cable so that says it is an older system.

Have you tried separately partitioning, and then using manual install?

---

### Post by dehiker on 2010-11-22
> **oldfred said:**
> Were you just installing Ubuntu to the entire hard drive? Is this an older system? What are its specs? I saw something about limiting IDE transfer due to 40 wire cable so that says it is an older system.
 
Have you tried separately partitioning, and then using manual install?
 
Thank you so much for your concious reply, oldfred!
Yes, I try to install Ubuntu to the entire hard drive, and also, the laptop is quite old, with only 256M RAM and 1.6GHz cpu. 
 
I'm sorry but what's "separately partitioning"? Usually, I manually partition the hard drive into / (5G), swap (100M) and /home (the rest 55G).
 
Also, I can install ubuntu 9.04 sucessfully. Maybe, it's really just because the laptop is too old. Thank you again for your kind help!
 
dehiker

---

### Post by oldfred on 2010-11-22
I think 256MB is the minimum and it should work. But I prefer 10GB as the minimum for / (root) unless you have real limits and then you can get by will as little as 4GB but it is difficult. With 256MB swap should be 2X RAM or 512MB.

Perhaps one of the lighter weight versions may run better.

Lighter weight Versions use with Chromium browser as it is lighter than firefox:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
Crunchbang: the unofficial Ubuntu Lite
Someone posted this:
Linux Mint XFCE runs fine on a PIII, 500 MHz
8 of the best tiny Linux distros
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang

---

### Post by dehiker on 2010-11-24
Thank you so much, olfred! Your suggestions is of great help, and lets me know there're so many wonderful tiny ditros.
And hope to get your help when I get some problems with ubuntu. Thank you again!

---

