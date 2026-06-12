---
title: "Upgrade from warty"
date: 2005-03-24
forum: Installation &amp; Upgrades
---

### Post by egorgry on 2005-03-24
Hi all. I'm brand new here but I've been using debian/sid for about five years. My system is a Dell inspiron 600m, Pentium 2ghz, 1 gig o ram, 64mb ati radeon 80gb HDD. ipw2200 wifi.

I receantly dist-upgrade form warty to hoary and everthing went extreamly well, even fixed up some acpi problems I had with teh system. My only issue is ever since the upgrade my processor is constantly spiking I looked at top and teh only thing taking up any resources is Xorg and it only hits about 30% at any time. The sytem ran fast and stable before. any tips or suggestions would be greatly apprciated.

Here was my method of upgrade.
cp /etc/apt/sources.list /etc/apt/sources.lists.warty
vi /etc/apt/sources.lis
:%s/warty/hoary/g
:wq!
apt-get update && apt-get dist-upgrade  

Thanks in advance and I look forward to teh future of this great distribution.

**EDIT** **FIXED**
I was playing with 3ddesk a neat desktop switcher and the 3ddeskd was the problem. pkill 3ddeskd and it's fixed. :)

---

### Post by orion_114 on 2005-04-09
I took 3ddesk off my system now and it is running way better !
Thanks for the post !

---

