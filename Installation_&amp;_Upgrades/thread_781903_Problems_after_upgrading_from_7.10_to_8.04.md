---
title: "Problems after upgrading from 7.10 to 8.04"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by antz321 on 2008-05-04
Hi,
I should first of all say that I am fairly new to ubuntu, so please talk in terms that I can understand :)

2 Problems I currently have with 8.04:

First of all, I am now unable to access the internet or my home network. It says it is currently connected to a wired network, yet the internet does not work. Any ideas?

Second problem is this. On the GRUB bootup screen, rarter than just being presented with ubuntu 8.04, recovery mode and vista, I am getting the following:

Ubuntu 8.04 Kernal 2.6.24-16 generic
Ununtu 8.04 Kernal 2.6.24-16 generic (recovery mode)
Ununtu 8.04 Kernal 2.6.22-14 generic
Ununtu 8.04 Kernal 2.6.22-14 generic (recovery mode
Memtest
Windows Vista

Why am I being presented with all these different options? I tried booting into 2.6.22-14 but the GUI does not function.

Thanks in advance.

---

### Post by macaholic on 2008-05-04
I'm not good with wireless drivers myself, but I would make a separate post about that in the Network and Wireless forum, but I can address your second problem. The different options at GRUB are the various kernels you have installed. The older kernel is from Gutsy and will not work on hardy. You can safely remove it via synaptic. (System > Administration > Synaptic Package Manager)

---

