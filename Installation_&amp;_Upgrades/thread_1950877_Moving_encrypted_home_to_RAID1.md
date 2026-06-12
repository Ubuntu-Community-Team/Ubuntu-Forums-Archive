---
title: "Moving encrypted /home to RAID1"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by diamond_D on 2012-04-01
I'm putting together a new home file server using Ubuntu 10.04. My box will start out with 2 x 1TB HDD's. 
SDA1 will contain all the OS files and mounts (including an encrypted /swap) and an extra partition to contain a Vbox VM.
SDA2 I want to place an encrypted /home as well as 2 other partitions for more VM's.

This will be a temporary configuration while I wait for my 2 x 2TB Hitachi HDD's to arrive off back order. 

When I get the 2 x 2TB drives I want to configure a software RAID 1. I have never did this before and would like some comments and suggestions regarding the best way to go about moving my encrypted /home over to the RAID 1 volume once it is configured.:mad: I am a n00b when it comes to working with encryption and RAID.

Thanks in advance.

---

### Post by Paddy Landau on 2012-04-02
Encryption is poorly documented and therefore difficult to work with.

My suggestion for the easiest method is to back up all your data; install Ubuntu on the new system (with an encrypted home); and restore your data after logging in.

---

