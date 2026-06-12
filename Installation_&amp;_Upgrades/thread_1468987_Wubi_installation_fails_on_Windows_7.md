---
title: "Wubi installation fails on Windows 7"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by vettypayal223 on 2010-05-01
I tried the "Install Inside Windows" with a Windows 7 Ultimate 32-bit version, using the default WUBI that came with the Lucid CD image (The finbal release version). My installation config is this

* I have Windows 7 installed on the first partition of SATA disk
* Wubi created loopback disk (root.disk) is on 2nd Partition

The Ubuntu splash shows up and goes up to "Checking for Network time servers" and then shows up an error message saying that root disk is not configured. This has happened with 9.10 as well where even the splash wouldn't show up, only the grub prompt will be shown. When I use Live CD, it all goes fine. But when I start up GParted fromt he Live CD, it says that there are no partition tables found on my disk. Could anyone please verify whether it's a problem with my hard disk config or is there anything that I'm doing wrong? Thanks.

---

