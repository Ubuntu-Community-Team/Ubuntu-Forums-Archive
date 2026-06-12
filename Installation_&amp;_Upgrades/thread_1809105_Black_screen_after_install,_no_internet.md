---
title: "Black screen after install, no internet"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by tuxor1337 on 2011-07-21
After ubuntu studio i386 install on my thinkpad x31, I'm getting a black screen on boot. ctrl-alt-F8 reveals the following:

```
mountall : Plymouth command failed
mountall : Disconnected from Plymouth                      
```via ctrl-alt-F1, I can log in to the console. But I was not able to set up an internet connection... (have to work on this, maybe later..)

But maybe there is a way to fix this without internet connection?

(Btw: This solution seems to rely on an internet connection:
[http://ubuntuforums.org/showthread.php?t=1651899](http://ubuntuforums.org/showthread.php?t=1651899) )

---

### Post by tuxor1337 on 2011-07-21
The problem persists. I can't configure any ethernet-devices (btw, I didn't during installation), because "ifconfig" doesn't show any devices, even though my devices are listed with lspci.

Oh please give me a hint. I have no idea what I could do about this without internet connection!

---

### Post by YannBuntu on 2011-07-22
Thinkpad x31 had a problem with Usplash with Ubuntu 8.04, we had to choose 1024 x 768 resolution. Maybe there is still a similar bug in last Ubuntu versions. (by the way, which Ubuntu version are you using ? 11.04 ?)

---

### Post by 2F4U on 2011-07-22
I am running Xubuntu 11.04 on a X31 without much problems. Ethernet worked automatically. There is a problem with the ATI card and KMS, which prevents the machine from waking up from suspend and hibernate. I worked around this issue by adding "nomodeset" to the grub line.

---

### Post by tuxor1337 on 2011-07-22
What I did now is: I discarded this broken installation and installed native Natty instead. Here, everything worked ootb. No idea, why ubuntu studio didn't work. Maybe the installation media was defective.

Now I'm having Ubuntu Studio running after having installed the ubuntustudio-desktop package.

Thanks for your help :)

---

