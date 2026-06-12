---
title: "Network interface problem after installing 8.10 intrepid ibex"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by olmox on 2008-11-05
Two weeks ago I bought a new desktop pc, with a mother board ASUS P5GC-MX 1333, with an integrated NIC (Attansic).

I installed on it a ubuntu 8.04.1 (desktop edition), a Debian lenny and a Windows Xp.

Every device was behaving regularly, and also networking was fully working.

Two days ago I wanted to test inttrepid ibex server edition, and so i installed on a separate partition of the same disk.

As a result, now I have that the network interface can't be recognised by no other o.s. than ubuntu 8.10 server edition!!

Ubuntu 8.04.1, Debian lenny and windows XP all work normally, but they can't see the NIC and so they can get no connection to the router.


I also tried with some live cd (ubcd4win, debian live, knoppix), but none of them can see this poor NIC.

Only intrepid ibex can successfully connect to the net.

Any hint would be precious!

thank you in advance 



                      olmox

---

### Post by Briga on 2009-01-16
I do have the same problem and I am researching it here and through Google. Basically on a dual boot PC with 8.04 and XP I wiped 8.04 to replace it with a fresh install of 8.10. 

All fine in 8.10 except that now in XP the network card is always "disconnected". Looking at the router I see that Intrepid actually "switch off" the card because the light goes off at the end of the shutdown (it doesn't with other SO). 

If I find more I will be back.....

Like look here:

[https://bugs.launchpad.net/ubuntu/+bug/296502](https://bugs.launchpad.net/ubuntu/+bug/296502)

If you boot in Ubuntu and reset the PC (with a button not using Ubuntu command) it works for me.... give it a try. 

Briga

---

