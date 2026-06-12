---
title: "Ubuntu 8.04 on Toshiba Laptop (PAIN IN THE ***)"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by rafaelbrandao on 2008-08-27
Hi guys, I have a L355-S7812 Toshiba Laptop and I simply cant get ubuntu installed on it... 

I have tried everything: setting SATA controller to compatibility mode (ACHI and Compatibility are available), different boot parameters (all_generic_ide floppy=off irqpoll) and I still cant install ubuntu. When I try with version 8.04 it crashs with:

run_program: '/sbin/modprobe' abnormal exit

and sends me to intramfs busybox ... Using version 8.04.1 it freezes after loading kernel...

Plz help!!! I cant stand windows vista anymore!!! :(

thankz in advance...

---

### Post by lavajumper on 2008-09-09
I've just loaded 8.04 onto an L305D-S5868 and was getting the same problem. I had to go into the BIOS and disable the onboard LAN.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/231226](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/231226)

and if you really feel ambitious

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749)



I'm working on getting the LAN working now. Maybe yours has the same issue. I'll post if I get it all going.

---

