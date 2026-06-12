---
title: "Can't configure internet!!"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Marce Acosta on 2009-08-18
Hi all, by now, I'm writing from MS WINDOWS because I can't configure internet in my fresh instrall of kubuntu karmic koala alpha 4.. see, the problem is my netmask is: 255.255.255.252 but it only lets me put a 2 digit number.. what can I do??:confused: thanks in advantage

---

### Post by dino99 on 2009-08-18
what says dmesg ( in a console )
or
system  --> administration  --> view log system
or
/var/log

how are you connected (dsl, cable, router, firewall) ?

in a console: give the output of ifconfig

---

### Post by wieman01 on 2009-08-18
Again, Marce, please do not post duplicate posts/threads. This is a 3rd one in a series, so please abide by the rules and post a single thread for one & the same problem only.

---

### Post by Marce Acosta on 2009-08-18
thanks all, but forget it.. I'll simply use gnome..  :neutral: :neutral: :neutral: :neutral: :neutral: :neutral: :neutral: :neutral:

---

### Post by jalmargyyk on 2009-08-18
You'll probably have to use the prefix format of mask 255.255.255.252 which is 30. For more info visit [http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

---

### Post by Marce Acosta on 2009-08-18
> **jalmargyyk said:**
> You'll probably have to use the prefix format of mask 255.255.255.252 which is 30. For more info visit [http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

Yes, just realized it says prefix, not netmask, but again. I put 30 as prefix, and didn't connect..  :evil::evil::evil::evil::evil::evil::evil::evil:

---

### Post by kenleyrob on 2009-08-18
i had problems with knetworkmanager in kubuntu karmic, so installed nm-applet from a gnome ubuntu cd and connect to the net using that for the time being. Make sure you kill the process knetworkmanager then install and run nm-applet.

---

### Post by Marce Acosta on 2009-08-18
Thank you! I'll install it..

---

### Post by Marce Acosta on 2009-08-18
does jaunty have the same problem??

---

### Post by kenleyrob on 2009-08-19
> **Marce Acosta said:**
> does jaunty have the same problem??

nope, and neither will karmic when it is released I assume. It is only Alpha stage now so you should expect things like this.

---

### Post by nnamdi on 2009-08-19
hello why safe yourself the strees and use a more stable distro ok i advice you use jaunty

---

