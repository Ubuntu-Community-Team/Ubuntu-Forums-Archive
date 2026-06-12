---
title: "Problem with booting"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by masonmop on 2005-06-27
after taking a friends advice I've been tried to install Ubuntu Linux 5.04 on my second hard drive (80GB), but it won't work (even after 4 tries).

Except for the first and last tries at installing it, the installation has gone straight to the end without a problem, it just won't reboot. It says it's installed the GRUB boot loader but when it reboots at the end of the install, it boots windows. I have list of a few things that I might have done wrong that could have stuffed up the installation. It's a long-ish list so make sure you have a bit of time. Some of the answers may seem a bit obvious, but i'm a bi of a newbie

First off, which 'locale' should I use? en_AU.UTF-8 or just en_AU? (I live in Australia, by the way)
Should I enable PCIMCA? I said no to that
After that it said that it could not load the modules ide-mod (Linux IDE driver), ide-probe-mod (Linux IDE probe driver), ide-detect (Linux IDE detection), ide-floppy (Linux IDE floppy)
It also said that simply proceeding with the install may make them available later.
It was unable to load them ,again, when detecting network hardware

What is my primary network interface? eth0 which is the one connected to the internet, or eth1 which is connected to the LAN?

When I'm repartitioning the hard drive what partition table should I use? I chose MSDOS, is that okay? What are primary and logical partitions?

Which kernel should I load? linux-amd64-generic, linux-image-amd64-generic, or linux-image-2.6.10-5-amd64-generic. (I use an AMD64 3000+)I chose the first one

Should I add another apt-source?

The rest works fine, except when it reboots. It's supposed to use GRUB to give me a choice between linux and windows, but it just loads Windows automatically.
Thank you in advance,
Ben

---

### Post by christooss on 2005-06-27
[QUOTE=masonmop]

When I'm repartitioning the hard drive what partition table should I use? I chose MSDOS, is that okay? What are primary and logical partitions?

[/QUOTE]
 When repartitioning create two partitions

/              -------- ext3 filesistem--------------primary
swap --------------swap(or something like that)---------------logical

For boot you can change windows boot.ini (Search this forum for dual boot)

---

