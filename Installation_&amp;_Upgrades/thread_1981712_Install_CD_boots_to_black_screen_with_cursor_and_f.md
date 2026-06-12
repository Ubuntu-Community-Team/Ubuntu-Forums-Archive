---
title: "Install CD boots to black screen with cursor and freezes"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by tkdncty2 on 2012-05-17
Hello!

I'm trying to install Ubuntu 12.04 LTS. When I put in the install CD and reboot, a purple splash screen comes up briefly, then it switches to a black screen with a blinking cursor and you can see the CD drive and the HDD working. This goes  on for about 1 minute, then the CD drive and the HDD stops working, that "ubuntu drum roll" sound is heard, the black screen with the blinking cursor stays and the computer hangs.

This happens with both 32 and 64 bit versions.

My computer is:

Inter Core 2 quad 2.66 GHz
4 GB RAM
200 GB SATA HDD
1 GB NVIDIA GeForce GTS 450


Do you know what the problem could be?

---

### Post by darkod on 2012-05-17
It should be video driver issue with nvidia. Look here how to boot with the nomodeset parameter, and if that loads the live desktop, you can install. But note that again on first boot you need to add the parameter to boot once, until you can install the driver once ubuntu is running from the hdd.
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by tkdncty2 on 2012-05-17
Thanks! That works.

---

