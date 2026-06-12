---
title: "New Laptop Install"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by kprowell on 2008-02-03
I just got a new laptop (HP Compaq 6910p) and I want to install Ubuntu on it.  I've used Ubuntu in the past (up to 7.04) but the latest version borked my old laptop so I waited for my new one.
 
My new one has Intel 965 graphics and I tried the live cd and I was not able to get 3d effects to work.  I've tried other distros with newer kernels (2.26.23+) and it works.  Does anyone know how to get it to work with the current version of Ubuntu 7.10?  Thanks in advance.
 
Regards,
 
Kevin

---

### Post by lswest on 2008-02-03
it should work if you load the proper intel drivers for your card, which doesn't occur on the liveCD if i remember correctly.  Best thing to do would be install it and test it:P

---

### Post by kprowell on 2008-02-03
I did just that...  I installed 7.10 and performed all the updates.  It runs really well except the 3d graphics and my wireless card.  I don't fully understand.  When looking at all the hardware installed, everything looks right.  It seems to identify all the hardware but it doesn't fully function.  For example, my wireless card seems to be working ( I can see wireless networks available) but when I try to connect (even unsecured) it doesn't.  And I as mentioned, compiz-fusion just plain doesn't work.  Thoughts/suggestions?

EDIT:  I did some more research and found a way to enable 3d effects fro the Intel 965.  You need to comment out the line in /usr/bin/compiz file that refers to the Intel 965.  It is blacklisted.  I did it and so far it works fine.  Now for the wireless issue.

EDIT:  I took a break shut down the laptop, came back a few hours later and it worked without doing a thing.  Weird.......

---

