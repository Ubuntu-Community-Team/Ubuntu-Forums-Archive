---
title: "Don't know how to install a certain kernel in Xubuntu 22.04 (to test bug #2062951)"
date: 2024-10-22
forum: Installation &amp; Upgrades
---

### Post by r.vanderspank on 2024-10-22
I have Xubuntu 22.04 (dual boot with win10) with kernel 6.8.0-48-generic.
I experience flickering when my mouse cursor is in the lower part of the screen. This is bug  #2062951 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062951)).
There is a fix (add "intel_iommu=igfx" to the grub), but they asked me to test another kernel which should fix this better.

Firstly I don't understand if I should install linux-xilinx/6.8.0-1009.10 or linux-hwe-6.11/6.11.0-9.9~24.04.1. There are messages of both in the webpage above. 
Secondly I don't know if this is possible in Xubuntu 22.04 and also how to do it.


I tried to install kernel 6.11 with the program Mainline kernels but I could not boot.
I tried "sudo su" and then (as in the website [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) to which they refer) command 
```
[COLOR=#333333]cat <<EOF >/etc/apt/sources.list.d/ubuntu-$(lsb_release -cs)-proposed.list
[/COLOR][COLOR=#333333]# Enable Ubuntu proposed archive
[/COLOR][COLOR=#333333]deb http://archive.ubuntu.com/ubuntu/ $(lsb_release -cs)-proposed restricted main multiverse universe
[/COLOR][COLOR=#333333]EOF[/COLOR]
```

Then I tried "[COLOR=#333333]sudo aptitude -t jammy-proposed", pressed "u", but then I could not find one of the two kernels there (and also no folder "proposed").

Can you please tell me if I can install this kernel on Xubuntu 22.04 and how to proceed. Thank you![/COLOR]

---

