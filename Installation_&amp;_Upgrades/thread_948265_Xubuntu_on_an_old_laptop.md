---
title: "Xubuntu on an old laptop"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by M!K3_$ on 2008-10-15
Hi,
I want to run *buntu on my old laptop

Clereon 550Mhz
64Mb RAM
4.7GB HD

i can't run the Live CD for xbuntu (i think because of lack of RAM).

I wanted to know if i used the alternate install CD, and just skipped Live, would the OS run properly?

---

### Post by Partyboi2 on 2008-10-15
With 64mb you could use the alternate cd to install, however you would find that the performance of the installed  xubuntu would be effected considerable with that much ram. You might be better to try [[COLOR=Blue]darn small linux [/COLOR]]("http://www.damnsmalllinux.org/")or put more ram in the laptop.

---

### Post by M!K3_$ on 2008-10-15
thanks, ya after i posted i found something called fluxbuntu, which is even more lightweight  than xbuntu. so i think i'll give that a shot.



thanks
mike

---

### Post by snowpine on 2008-10-15
I would not personally recommend any of the 'Buntus for 64mb of ram. Your best bets are DSL (Damn Small Linux) or possibly Puppy. If you can upgrade your ram, it will open up more options (I would recommend 256mb minimum for Xubuntu), though your processor is a bit on the slow side. Good luck!

---

### Post by M!K3_$ on 2008-10-27
i am trying to get debian working because i can customize it to fit my needs very easily, but i am having problems with my wireless. i'll figure it out though.

for the record, i hate damn small.
i have never tried puppy though...


thanks for help
-M

---

### Post by kerry_s on 2008-10-27
> **M!K3_$ said:**
> i am trying to get debian working because i can customize it to fit my needs very easily, but i am having problems with my wireless. i'll figure it out though.

for the record, i hate damn small.
i have never tried puppy though...


thanks for help
-M

DSL can teach you a lot when you take the time to learn it.

use the debian net installer to install just the base.
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso)

at the package selection part, uncheck everything.

when the install is done, log in as root:
apt-get install xorg what-ever-else

you want xorg before anything else, if your going to use gui.

i use> 
apt-get install xorg jwm rox-filer leafpad sudo rungetty synaptic menu

for the start of mine.
my laptops 450mhz 256mb ram.

---

### Post by lisati on 2008-10-27
I tried a couple of flavours of *ubuntu on an older machine with 64Mb, but without any joy.....

---

### Post by robert shearer on 2008-10-27
Puppy might do it.

[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

