---
title: "need help re-installing ubuntu on a partion (what about Swap?)"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by rapidvictory on 2012-06-23
so im dual booting ubuntu 12.04 and windows 7 and i really dont like unity i want to go back to 10.04 (still have the disc conanical sent me). i have a series of questions. i know the support for lucid has ended but if i install it, will i still get all the updates that have come out until they stopped supporting it? whichever version i end up installing do i have to delete the swap partition everytime? or can i keep the same one no matter which version of ubuntu or distro i use (ive also had my eye on debian 6). thanks, sorry for long question!

---

### Post by David Andersson on 2012-06-23
> **rapidvictory said:**
> so im dual booting ubuntu 12.04 and windows 7 and i really dont like unity i want to go back to 10.04 (still have the disc conanical sent me). 

An alternative would be to keep 12.04 and use the Classical interface instead of the new Unity interface.

> **rapidvictory said:**
>  i know the support for lucid has ended but if i install it, will i still get all the updates that have come out until they stopped supporting it? 

Lucid Lynx 10.04 LTS is still supported. The desktop version will be supported until April 2013.

EDIT: About swap: Most, if not all, linuxes can use the same swap partition (not simultaneously of course, but that is not a problem between installs or when dual boot).

---

### Post by ranger1021994 on 2012-06-23
1 : You should get updates till the moment support ended..As in further development must've been terminated..but past developments are available.
2 : Swap remains intact since swap is just a termporary space eg. like a RAM (slow one :P)
3 : Try debian 6 on virtualbox before installing on ur HDD.See if you are satisfied with it. :)

---

### Post by rapidvictory on 2012-06-23
thanks for responding quickly! you've helped alot!

---

### Post by rapidvictory on 2012-06-23
thanks for the help. i've had lots of problems with 12.04 (update problems,PPA software not showing up, hassles with themes and overall the dash gets in the way and is slow on my machine, i simply dont need it)

the only downside to going back to lucid is that my internal laptop speakers dont work at all and ive tried everything, they work with any release after that but not with lucid (but i can manage) 


so when i install lucid i should just let it format the ubuntu partition and leave swap alone?


Edit:  im dualbooting with windows 7 so what about GRUB? is it going to just handle it by itself or do i have to configure something?

---

### Post by David Andersson on 2012-06-29
> **rapidvictory said:**
> 
so when i install lucid i should just let it format the ubuntu partition and leave swap alone?

That should work. If you have documents in /home, save them somewhere else first.

> **rapidvictory said:**
> 
Edit:  im dualbooting with windows 7 so what about GRUB? is it going to just handle it by itself or do i have to configure something?

Ubuntu installs grub by default. It should recognize the existing Win7 automatically and make a dual boot setup. (During install you can tell it not to install grub. Then you have to do it yourself later. Or if Ubuntu failed to install grub correctly.)

---

