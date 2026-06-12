---
title: "GRUB error 21"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by polemides on 2007-01-17
I am having the GRUB error 21 hang my newly installed ubuntu 6.06 lts. Windows XP is on hda (master), and I have installed ubuntu on hdb (slave). When I try to use the recover feature on the live cd, I get the same error. What do I need to do to get GRUB to work, or is there another solution. I want to migrate totally to ubuntu, but I still need to use XP for a few things. Thanks.

polemides

---

### Post by polemides on 2007-01-17
> **polemides said:**
> I am having the GRUB error 21 hang my newly installed ubuntu 6.06 lts. Windows XP is on hda (master), and I have installed ubuntu on hdb (slave). When I try to use the recover feature on the live cd, I get the same error. What do I need to do to get GRUB to work, or is there another solution. I want to migrate totally to ubuntu, but I still need to use XP for a few things. Thanks.

polemides
OK. I googled the problem and found a post that advised making the ubuntu drive the master so that GRUB would not be writing to the XP MBR. This worked and I am now happily proceeding.

polemides -  auton sunllambano

---

