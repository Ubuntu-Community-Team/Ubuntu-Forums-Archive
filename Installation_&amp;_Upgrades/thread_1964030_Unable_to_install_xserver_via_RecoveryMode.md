---
title: "Unable to install xserver via RecoveryMode"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by zogato on 2012-04-23
I made the stupid mistake of purging xserver from my system a while back and now I am unable to get it back. As it turns out, my previous problem had to do with flgrx and I had no need to purge xserver-xorg. 

Now when I try to get it back, via recoverymode for Ubuntu 11.04. I can't get any internet at all to complete a simple

sudo apt-get instal xserver-xorg 

Is there any solution to this? Or even the network issue? I want to avoid having to reinstall the entire system just for xserver.

---

### Post by zogato on 2012-04-23
I found out the problem. I'll post the solution in case someone else ends up with the same problem or similar.

Simply, I had to run *sudo dhclient eth0* to get an ip from the server I was connected too.

---

### Post by 9kkmin on 2012-06-03
Help me mate...! i have the same problem, i purged xserver in my endeavour to get compiz working,i can only access the terminal through the recovery mode and cant access the internet to install xserver

---

