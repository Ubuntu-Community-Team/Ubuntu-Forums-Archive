---
title: "kernel loading problems on my laptop"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by henac84 on 2006-02-25
Hello all!
Very new to all this so sorry for posting this query in random places earlier!
I have a Philips Freevents laptop running XP. The Live CD or Install CD arent work on my machine. I get to the screen which says Uncompressing Linux... Ok Booting from the kernel and then it stops! Same problem with both CDs. I tried doing everything on page [https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
which basically describes methods to boot Ubuntu without using any removeable media. Same problem remains! Please help!!

Specs follow:
Processor Type INTEL PENTIUM M
Processor speed 1.73
Operating system XP HOME
Memory Type DDR 333
Hard Drive Capacity 60
Memory Size 1024
Graphics Card Type INTEL GMA900
Graphics Memory 128mb shared
Sound Type AC97 16bit
Modem Type 56k
Other Interfaces WIFI 802.11b/g

---

### Post by cilynx on 2006-02-25
Which release of Ubuntu are you working with? (Hoary, Breezy, Dapper?)  Some of the releases just don't like some computers.  One of my machines at work (a Gateway) refuses to boot the Breezy install or Live CD, but does just fine with Hoary or Dapper.

---

### Post by henac84 on 2006-02-25
hi.. thanks for the reply.. my cd and covers just say ubuntu version 5.10 for your PC..!

---

### Post by cilynx on 2006-02-25
5.10 is Breezy.  You might want to try the Dapper Flight 4 (pre-release) CD and see if that gets you anywhere.

[http://cdimage.ubuntu.com/releases/dapper/flight-4/](http://cdimage.ubuntu.com/releases/dapper/flight-4/)

---

### Post by henac84 on 2006-02-25
[QUOTE=cilynx]5.10 is Breezy.  You might want to try the Dapper Flight 4 (pre-release) CD and see if that gets you anywhere.

[http://cdimage.ubuntu.com/releases/dapper/flight-4/](http://cdimage.ubuntu.com/releases/dapper/flight-4/)[/QUOTE]
I downloaded dapper.. same problem...

---

### Post by henac84 on 2006-02-25
I tried booting with the parameter pci=noacpi and everything seems to work.. :) 
does anyone know why that worked? i dont quite kno what made me try it..

---

### Post by xagoras on 2006-05-18
I have the same problem. I have a "PHILIPS freevents X30ES" and i try knoppix a it dont work. I tried > the parameter pci=noacpi but it tell me: "Kernel panic - not syncing: No init found. Tray passing init= option to kernel" What does this messenge means? What could i do?

Thank you very much.

Xagoras.

---

