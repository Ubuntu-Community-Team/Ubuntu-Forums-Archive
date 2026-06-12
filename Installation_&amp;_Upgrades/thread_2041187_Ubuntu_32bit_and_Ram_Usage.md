---
title: "Ubuntu 32bit and Ram Usage"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by IReadTheManual on 2012-08-12
There is often a cap of 4GB of RAM on a 32bit architecture using direct memory access, but there are also very spiffy and clever methods to use, albeit less efficiently, an unlimited amount of RAM. Can Ubuntu 12.04lts 32bit make use of these clever methods, and if so, how efficiently? I ask because I am deciding whether I need to upgrade from x86 install to the 64bit one.

---

### Post by 2F4U on 2012-08-12
I don't know exactly what you are looking for, but Ubuntu has PAE to allow the system to use more than 4 GB of RAM:

[https://help.ubuntu.com/community/EnablingPAE/](https://help.ubuntu.com/community/EnablingPAE/)

---

### Post by IReadTheManual on 2012-08-12
> **2F4U said:**
> I don't know exactly what you are looking for, but Ubuntu has PAE to allow the system to use more than 4 GB of RAM:

[https://help.ubuntu.com/community/EnablingPAE/](https://help.ubuntu.com/community/EnablingPAE/)

That's exactly what I was looking for. Thanks!!

---

### Post by sanderj on 2012-08-12
> **IReadTheManual said:**
> That's exactly what I was looking for. Thanks!!

As far as I know, the 32-bit Ubuntu installer of recent Ubuntu versions will automagically install the PAE-version of the kernel if you have at least 3GB RAM.

To know everything about your memory and system, you could run this:

```
wget http://www.appelboor.com/dump/check-my-memory.py
python check-my-memory.py 
sudo python check-my-memory.py
```

HTH

---

### Post by Cheesemill on 2012-08-12
> **sanderj said:**
> As far as I know, the 32-bit Ubuntu installer of recent Ubuntu versions will automagically install the PAE-version of the kernel if you have at least 3GB RAM.

As of Ubuntu 12.04 the PAE kernel is always installed, no matter how much RAM you have (although Lubuntu still installs the non PAE kernel).

---

### Post by sanderj on 2012-08-13
> **Cheesemill said:**
> As of Ubuntu 12.04 the PAE kernel is always installed, no matter how much RAM you have (although Lubuntu still installs the non PAE kernel).

Thank you for that info. Seems like a clever decision by Ubuntu ... oh wait: PAE is now always required:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_requirements](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_requirements) says:

> The Ubuntu 12.04 installation image does not include support for old computers that do not support PAE. If your computer is affected, you can either first install Ubuntu 10.04 or 11.10 and upgrade to 12.04 or you can use the Lubuntu or Xubuntu images. The non-PAE version of the Linux kernel will be dropped completely following the 12.04 release.


... I already bumped into some posts complaining their old CPU (without PAE) is not supported anymore by a fresh install of Ubuntu 12.04. Too bad for them.

---

### Post by 2F4U on 2012-08-13
There seems to be some contradicting information about PAE. This document suggests that a PAE kernel is only installed if a network connection is present during the installation from a liveCD:

[https://help.ubuntu.com/community/EnablingPAE/](https://help.ubuntu.com/community/EnablingPAE/)

This suggests that the default kernel for 12.04 is non-PAE.

---

### Post by Cheesemill on 2012-08-13
> **sanderj said:**
> ... I already bumped into some posts complaining their old CPU (without PAE) is not supported anymore by a fresh install of Ubuntu 12.04. Too bad for them.
You can always download the non-PAE version of the Mini CD and install a Ubuntu system from that if you have this problem.
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

---

