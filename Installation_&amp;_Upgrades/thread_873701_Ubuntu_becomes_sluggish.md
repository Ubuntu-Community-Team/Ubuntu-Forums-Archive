---
title: "Ubuntu becomes sluggish"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by nexist on 2008-07-29
I just installed Ubuntu Studio 64 bit 8.04

My system is a Intel Q6600 with 4 gigs of ram. I set it up with an 8G Swap File and about 230G for /.  After a while, the exact moment varies, it will start to bog down. The mouse (a razer deathadder) starts to jump as it plays catch up. Keypresses are not recognized if they come too close together. Top reports a lot of softirq (various types) which I do not see in my Ubuntu Server (32-bit) install.

Can someone tell me what is going on? If I reboot the problem returns. I have an Audigy and GeForce 9600 installed as well.

---

### Post by nexist on 2008-08-05
I Installed standard Ubuntu and it has not yet demonstrated this behavior.

---

### Post by Hyper Tails on 2008-08-05
try this if this helps

```
sudo dpkg --configure -a
```

---

