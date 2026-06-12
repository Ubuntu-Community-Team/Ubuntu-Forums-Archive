---
title: "upgrading to 3.16 kernel caused kernel panic"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by eli_fabrikant on 2015-01-20
Hello!

my RTL8723BE PCIe Wireless Network Adapter gives me loads of trouble (disconnects and freezes every few minutes), and from researching in the forums i understood that the issue might be solved in the new kernel version 3.16 (I currently use 3.13).

 I tried to upgrade to the new kernel according to the instructions here:
[http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/](http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/)

But when I reboot i can't get into linux and I get 'kernel panic' messages. 

What are my next possible steps? How can i upgrade without causing this mass?

I'm a novice so I really shoot in the dark all the time, so it would be great if you could help or direct me to a easy instructions (I couldn't find anything that I could understand)


thanks!
e

---

### Post by steelsoul on 2015-01-21
Hi, eli_fabrikant,

it is usually means that you forgot update your kernel modules. 

Take a look on the [https://github.com/alfredobonino/lnextinst](https://github.com/alfredobonino/lnextinst). There are post install utility, hope this helps you.

Best regards, 
steel

---

