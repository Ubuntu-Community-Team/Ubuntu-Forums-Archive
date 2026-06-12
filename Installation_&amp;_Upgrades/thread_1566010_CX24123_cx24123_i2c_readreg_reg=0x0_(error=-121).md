---
title: "CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by jabrown65 on 2010-09-01
After upgrading to Lucid I started getting this error during boot up:

[   12.208847] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)
[   12.208893] CX24123: wrong demod revision: 87

Ubuntu continues to boot and seems to work fine (although I am having an intermittent (!) disk mounting problem on a SATA drive, but I assume that is unrelated to this error)

I can't find anything meaningful about this when I search. What does this error mean? What info should I post to help make sense of it (moderate user).

John

---

### Post by jabrown65 on 2010-09-21
I fixed this problem by installing the latest driver for my HTDV video capture card. (Note: The driver that was installed by default by Ubuntu Lucid was not the latest version)

---

### Post by Bazon on 2010-10-18
Where did you get that driver? I got exactly the same message.

---

### Post by jabrown65 on 2010-10-28
Actually, I need to retract that "Solved" status. I am still getting the error message too. I thought my solution had worked, but either it didn't or it has reappeared.  Basically I googled the driver for my particular HDTV capture card, then followed the instructions to install it. But as I have said, this doesn't seem to have fixed the error. However, my system seem to be functioning perfectly, capture cards and all, so it doesn't appear to be causing any problems.

---

