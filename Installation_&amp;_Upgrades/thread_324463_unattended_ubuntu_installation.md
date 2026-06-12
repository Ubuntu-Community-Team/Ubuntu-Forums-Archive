---
title: "unattended ubuntu installation"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by ukasz20 on 2006-12-23
hi

i was wondering is there any way to make ubuntu installation unattended.
verry important for me is to set swap space and what programs will be installed.
everything has to be on ubuntu server

i tried bootcd program but it turned realy messy.
 
any ideas ?

---

### Post by wpshooter on 2006-12-23
If possible at all, I would say that what you are wanting to do would be more trouble than it would be worth.  And beside that, IMO, the installation of ANY operating system should be OBSERVED by the installer (that means a human person) to make sure that everything goes as it should during the installation.

We still have not gotten to the point in time like on STAR TREK that we can completely turn our lives over to a computer system.

---

### Post by K.Mandla on 2006-12-24
> **ukasz20 said:**
> hi

i was wondering is there any way to make ubuntu installation unattended.
verry important for me is to set swap space and what programs will be installed.
everything has to be on ubuntu server

i tried bootcd program but it turned realy messy.
 
any ideas ?
It is possible, although it seems rare around here. There are some instructions [here]("http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html") that might interest you, although they are slightly dated. It's definitely something that you'll have to experiment with. Good luck!

---

### Post by KeighleHawk on 2007-01-12
We are also looking at a Sourceforge project called 'Unattended'

[http://sourceforge.net/projects/unattended/](http://sourceforge.net/projects/unattended/)

Right now we are focusing on our Windows burden though so have not gotten to trying Linux distros with it...

Robert Kuropkat

---

### Post by ukasz20 on 2007-01-12
Mandla thx for that but that exampe config file is not enough. i mean it doesn't have all the docs. if i want to partition disk for example 512 mb for swap and rest for / the examples doesn't cover everything about that what to write to that cfg file :( 

i have managed to do everything i want through bootcd program. i don't know why it has problems with usb. and the kernel witch will install on hd ( after installing from bootcd) have so many errors.

thx anyway

---

