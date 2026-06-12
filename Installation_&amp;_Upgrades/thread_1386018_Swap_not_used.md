---
title: "Swap not used"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by mkalbere on 2010-01-20
Hello !
Got a karmic installed on a eeepc 1201.

It randomly crashs, and I try to identify why ... 

One possibility is a missuse of the swap.  Even if I stress my system, the swap remain at 0k, which doesn't seems to me to be a "normal" behaviour 

Mem:   1797372k total,  1518124k used,   279248k free,    74548k buffers
Swap: 10233364k total,        0k used, 10233364k free,   987916k cached

I tried to tweek the swapiness to low or high value, but I get no changes
sysctl vm.swappiness=80
or 
sysctl vm.swappiness=20

Reformating (mkswap) didn't change any thing ... any idea ?

---

### Post by fromthehill on 2010-01-20
it still has 272MB memory left

you really don't want your computer to use swap space when it's not necessary

according to what I can find about the "sysctl vm.swappiness" command it is only used if the ram is actually full.
also the command you used isn't permanent. 
you need to add "vm.swappiness = 20" to /etc/sysctl.conf
and then reload it with: /sbin/sysctl -p

---

### Post by mkalbere on 2010-01-20
thanks for the reply.
Yes I know (there is some RAM left) but it doesn't change even if I stress my system by opening 20 different app.
Moreover, I checked with my "normal" desktop (also a 64bit ubuntu system), that have 4G of ram, even at the start up some swap is used.

---

