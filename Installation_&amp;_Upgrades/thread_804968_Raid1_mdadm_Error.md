---
title: "Raid1 mdadm Error"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by jolyan on 2008-05-23
Hi

Banging my head against a wall and can't find a applicable gem that provides a solution, so finally it's a post and hope.

I have three drives, two SATA and one IDE, mb only has two sata io.

One sata is my boot/ubuntu drive and the idea is to use the remaining sata and ide as a raid1 configured data store. Both are 250Gb with a single partition.

'sudo mdadm --create /dev/sdc1 --level=1 --raid-devices=2 /dev/sda1' gives the mdadm error message 'you haven't given enough devices (real or missing) to create this array'

I am an ubuntu baby so please be gentle.

Ta.

---

