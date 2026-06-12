---
title: "How to install windows XP on top of ubuntu 10.10?"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by pavelexpertov on 2011-01-30
I cleared my mate's hard drive with windows xp and then i installed ubuntu on a clear hard drive. Now, my mate wants to have two systems on the hardrive and he wants to put windows xp. How do i do it?!

---

### Post by dino99 on 2011-01-30
here is what you need about ubuntu:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

then, depending on free hdd space, you can either:

- install virtualbox 4 on ubuntu and have xp as a guest
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

- use a formatting tool (partedmagic for example) to resize your actual partition(s) to make room for xp

sidenote: xp is on end of life anyway and is still a virus/trojan/malware/... entry. Mostly all exe apps run on ubuntu using wine (winehq) [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

myself have no more xp or else for years now and i still run exe apps without issues. Note that you have free software high quality equivalent ready to be installed into synaptic.

---

### Post by kansasnoob on 2011-01-30
> **pavelexpertov said:**
> I cleared my mate's hard drive with windows xp and then i installed ubuntu on a clear hard drive. Now, my mate wants to have two systems on the hardrive and he wants to put windows xp. How do i do it?!

What version of Ubuntu? I mean 10.04, 10.10 :confused:

This still works other than the parts regarding grub if you're using a current version of Ubuntu:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

**So ignore page 2 and page 5!**

To recover the grub bootloader you'll need to follow this guide:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I prefer method #3.

---

### Post by pavelexpertov on 2011-01-30
Yeah thanx dino99, but i am doing it for my mate to be honest, but i got two systems anyways. Plus, thanx kansasnoob and the version of ubuntu is 10.10.
I can create partitions by using gparted in ubuntu, but when i will create a partitin and install windows xp "straight" on it, will ubuntu configure grub so i can use dual boot to choose between two systems when i start up a computer? That really concerns me...:---)

---

### Post by pavelexpertov on 2011-02-08
hey guys, i have done one experiment and i could reinstall grub 2 to dual boot between windows xp and ubuntu 10.10...... but data that was on ubuntu 10.10 was disappeared after widnwos was installed. I used this [guide]("http://https://help.ubuntu.com/community/Grub2") to reisntall grub 2.

---

