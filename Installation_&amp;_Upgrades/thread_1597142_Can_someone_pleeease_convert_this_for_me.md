---
title: "Can someone pleeease convert this for me?"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by tigerking615 on 2010-10-15
Hey guys,

I'm trying to install the UC Berkeley variant of Scheme (programming language) on my computer for one of my classes, but it won't work. I'm pretty sure it's because of this note on the instruction page:
> For Debian GNU/Linux on a pure64 (amd64) system: 
	Use a 32-bit computer to 'alien STk-4.0.1-ucb1.3.6.i386.rpm'
	On the 64-bit computer, run 'apt-get install ia32-libs'
	copy the $STK.deb file from the 32-bit computer to the local amd64, ie:
	'scp [email]user@32bHost:~/$STK.deb[/email] root@local64bHost:~/.'
	On the 64-bit computer, run 'dpkg --force-architecture $STK.deb'

Since I don't have access to a 32-bit computer with Ubuntu, can someone please use Alien to quickly convert the RPM file into a .deb and post it back here? 

[Link to the RPM file](http://wla.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm)

Thank you!

---

### Post by tigerking615 on 2010-10-15
This is going to sound really dumb, but I can't download that. Why can't you attach it here, and why does your link keep linking me to sketchy stuff?

Can someone else please help me out with this? It just takes a minute to convert a 2MB file.

---

### Post by TNT1 on 2010-10-15
I'm just installing alien. will do it for you now.

---

### Post by TNT1 on 2010-10-15
[http://jump.fm/AYOJT](http://jump.fm/AYOJT)

---

### Post by tigerking615 on 2010-10-15
Got everything working. You are amazing, thank you!

For you:
[img]http://www.contrib.andrew.cmu.edu/~rkhosla/cookie.jpg[/img]

---

