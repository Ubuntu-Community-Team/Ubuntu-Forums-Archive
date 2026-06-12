---
title: "VMWare Player 4.0.1 won't run on Ubuntu 11.10 64-bit with kernel 3.0.0-14-generic"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by T1Oracle on 2011-12-14
I installed VMWare Player 4.0.1, but when I try to run it I get a prompt that tells me "Kernel headers for version 3.0.0-14-generic were not found" and it asks me to specify the location of the headers.  When I select "/usr/src/linux-headers-3.0.0-14-generic" it says:
"C header files matching your running kernel were not found.  Refer to your distribution's documentation for installation instructions."

What am I supposed to do?

I searched for everything I could find about kernel headers and I installed a ton of crap I probably don't need and is still doesn't work.

Any help is appreciated. Thanks.

---

### Post by T1Oracle on 2011-12-14
Should I just use 10.04LTS? This is costing me money not having a working machine for my business.

---

### Post by T1Oracle on 2011-12-16
Well, I was really hoping at becoming proficient in VMWare but given this issue I have no choice but to switch to VirtualBox.  Hopefully it runs my Vista VM.

---

### Post by azmyth on 2011-12-16
It works for me. You must not have the proper headers installed. Install the linux-headers-3.0.0-14-generic package.

---

### Post by T1Oracle on 2012-01-05
> **azmyth said:**
> It works for me. You must not have the proper headers installed. Install the linux-headers-3.0.0-14-generic package.

sudo apt-get install linux-headers-3.0.0-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.


:(

---

