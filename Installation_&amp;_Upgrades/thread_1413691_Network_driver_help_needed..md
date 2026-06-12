---
title: "Network driver help needed."
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by uRock on 2010-02-22
I just installed Ubuntu 9.04 on a Netbook. The Alternate installer did not recognize the wired NIC and therefore didn't install any drivers to make the wireless nor wired NICs work. What do I have to install to get these to work? Please keep in mind that it will not connect, so the driver needs to be on the disk.

Thanks8-)

[SIZE="5"][COLOR="Red"]Searchers! See post 9 for the fix to this problem![/COLOR][/SIZE]:P

---

### Post by uRock on 2010-02-22
I have checked Synaptic and it appears that everything is installed for the network. I am stumped here. I have the LAN wired, the router shows that it is connected, but nothing works.

---

### Post by ubunterooster on 2010-02-22
have you gone to system/administration/hardware drivers?

---

### Post by uRock on 2010-02-22
Yep. Would I be better off burning another ISO and reinstalling?

---

### Post by ubunterooster on 2010-02-22
Probably. I would reccomend Moblin or eeebuntu as a netbook OS esp. as these have BETTER (not perfect) drivers for netbooks, esp. for wireless cards. [I've done a lot of distro-hopping]

---

### Post by uRock on 2010-02-22
Cool, thanx.

---

### Post by ubunterooster on 2010-02-22
Not a problem. Just tell us which you decide to use and if it fixes the problem.

---

### Post by uRock on 2010-02-22
> **ubunterooster said:**
> Not a problem. Just tell us which you decide to use and if it fixes the problem.

Will do. I booted the Jaunty LiveCD and it did not support the NICs. When I installed, I used the alternate disk for encryption, so I didn't get to check. Not to mention, I had faith it would work.

---

### Post by uRock on 2010-02-24
Jaunty does not seem to support this Netbook's NICs. But, the fix below will get the connection tuned on Karmic.

Entering the following code into a terminal fixed my problem.```
sudo apt-get install linux-backports-modules-karmic
```
I found the fix here [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

