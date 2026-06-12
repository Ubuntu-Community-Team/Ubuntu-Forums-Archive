---
title: "Issues getting Ubuntu Installed as CPU has no PAE Support"
date: 2019-07-10
forum: Installation &amp; Upgrades
---

### Post by KenUBF on 2019-07-10
I recently got an old Gateway laptop that still has Windows XP on it and I was hoping to install some flavor of Ubuntu on it, but whenever I try to boot one of the 32-bit iso's it tells me my CPU doesn't support a PAE kernel. Would it be possible to install a different kernel? Or is there a Linux distro that would work for my situation? The system has an i686 Intel processor, only 992MB of RAM and a 93GB hard drive.

---

### Post by Impavidus on 2019-07-11
The last version/flavour of Ubuntu that supported a non-pae kernel was Xubuntu 12.04, which is long dead. Some processors (Pentium M, Celeron M) support pae but don't tell so. Lubuntu can be installed on those using forcepae: [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

In other cases, maybe there is a different distro for really old hardware.

---

### Post by KenUBF on 2019-07-11
Thank you for your help Impavidus. It looks like I found a solution on askubuntu here: [https://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](https://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

I used the 4th workaround listed, typing in -- forcepae -- at the bootscreen and all went smoothly from there. I installed Xubuntu and it works well.

---

