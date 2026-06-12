---
title: "karmic, network-manager, and rt2500"
date: 2009-07-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joepotter on 2009-07-19
I have my wife's computer running 64bit Jaunty and her rt2500 card works OK. 

So I put an identical card in my tower which is running 64bit karmic. I have the 0.7.1 applet in the upper right hand corner. It says "Auto eth1" (or I would have to write this on the Mac. The "wired network" is greyed out as is the "Wireless Networks" portion.

If I run sudo iwconfig; the box sees the unconnected card.

The questions are: does network manager work under karmic at this time? Will it work with an rt2500 card? How should I proceed from here? Should I just configure the card manually?

(by the way, I do have it connected by eth1 now, but I need to move the router and use the wireless card.)

---

### Post by woodbj on 2009-07-20
I think you may be affected by this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417)

---

### Post by joepotter on 2009-07-20
Thanks for the heads up. It is just my luck to always try something just as it is fouled up. 

Oh well, perhaps it will be fixed soon.

---

### Post by nperry on 2009-07-20
> **joepotter said:**
> Thanks for the heads up. It is just my luck to always try something just as it is fouled up. 

Oh well, perhaps it will be fixed soon.

I believe the fix has been tested and will be push upstream (if not already!)

---

### Post by joepotter on 2009-07-21
> **nperry said:**
> I believe the fix has been tested and will be push upstream (if not already!)

How will I know when this is thought to be fixed? Will it be with the next kernel update?

I tried a new type N wireless card in this box just yesterday and it worked "out of the box". Brand new gear without a single linux recommendation that I could find and it works out of the box. My rt2500, not so much.

Oh well, the joys of computing.

---

