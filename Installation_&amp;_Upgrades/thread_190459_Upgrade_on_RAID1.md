---
title: "Upgrade on RAID1"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by bruma on 2006-06-06
I want to upgrade Breezy (with apt-get) which is installed on sw RAID1 with two devices, md0 is / md1 is /var. I notice in [Release notes]("http://www.ubuntu.com/download/releasenotes/606") 
> If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.
that RAID array should be stoped, disabled.

Is this true also for apt upgrade?
How can I upgrade if I disable array for root /?

---

