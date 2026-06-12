---
title: "installed karmic via debootstrap - no ssh (access denied)"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by vel_tins on 2010-03-17
Hello,
first, sorry for my english..:P
What I did:
I followed this howto to install Karmic from Karmic via debootstrap:
[https://help.ubuntu.com/9.10/installation-guide/i386/linux-upgrade.html]("https://help.ubuntu.com/9.10/installation-guide/i386/linux-upgrade.html")
so far so good...this bootstrapped karmic boots and I can connect to the openssh server, but when I try to login, it gives me "access denied".
I can login from the original Ubuntu via "chroot" ssh root@localhost, but not from "outside".
So I think, debootstrap is not the best solution, to setup a new Ubuntu from scratch.
Background: my Server is far away from me and only accessible via SSH/VNC.
But  this server, its an upgraded Ubuntu from 8.10 to 9.04  to 9.10, with some errors, I couldnt fix, so I thought a fresh install would be a better solution.
So I connected to him and "debootstrapped" a new install on a separate partition, installed openssh-server, but always "access denied"
Maybe somone has a better solution to setup an Ubuntu server from scratch, via "remote install" or maybe a copied "VMWARE" install?
thanks for your answers

---

