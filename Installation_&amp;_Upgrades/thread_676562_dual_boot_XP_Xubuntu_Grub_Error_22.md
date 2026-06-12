---
title: "dual boot XP Xubuntu Grub Error 22"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by smacd on 2008-01-23
I am trying to set up my system to dual boot XP and Xubuntu. I have 4 hard drives in my system, a total of 5 partitions. I have an existing copy of XP on the one drive that has 2 partitions, and I have just tried to install Xubuntu on one of the other drives.

Now, when I try to boot up, it gets to GRUB and gives me "Error 22" and stops. I have tried booting up with just the livecd, and going into a terminal and typing:

```

> sudo grub

> find /boot/grub/stage1
(hd2,5)
> root (hd2,5)
> setup (hd2)

```

and then trying a reboot, however I am still getting Error 22 when GRUB loads.

Any advice?

---

### Post by Partyboi2 on 2008-01-24
This will explainn grub 22 error better and give you some ideas on how to address the problem
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

