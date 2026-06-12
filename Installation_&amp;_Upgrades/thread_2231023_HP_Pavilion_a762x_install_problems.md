---
title: "HP Pavilion a762x install problems"
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by mark144 on 2014-06-22
Looking for assistance on my problem. I have installed various Linux OS's on various computers. I recently tried converting over an old pc, it is an HP Pavilion a762x desktop computer. It had Windows XP and a 32 bit system. I downloaded the 32 bit Ubuntu, created the startup disk on my 32 GB USB, and tried to install it as I have always done. The USB ports on the Pavilion are 2.0, Ubuntu setup sometimes starts, and I always get the error message "this kernel requires an x86-64 cpu but only detected an i686 cpu". I have done countless hours of various solutions, searching for answers, and trying anything. I have tried to "enable virtualization" in BIOS, however that is not an option on my system. I cannot access any kind of OS because the computer was wiped. I have also tried a 64 bit, even though I know it isn't right, and still receive the exact same result. I hope I have provided enough information and someone out there can help me. Thank you in advance.

---

### Post by Vladlenin5000 on 2014-06-22
Hi, welcome :P

This error message
> **mark144 said:**
> I always get the error message "this kernel requires an x86-64 cpu but only detected an i686 cpu". 
could only come from a 64-bit Ubuntu installer. You better check whatever you downloaded in the first place. You need the "ubuntu-14.04-desktop-i386" ISO for 32-bit architectures. "ubuntu-14.04-desktop-amd64" ISO is for 64-bit.

---

