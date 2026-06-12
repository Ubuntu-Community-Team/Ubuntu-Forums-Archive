---
title: "How to bypass partition and mount during install?"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by heldal on 2012-05-06
Is there a way to start the installer so that it bypasses disk partitioning and mounting? 

I'm about to convert a 10.10/32 system to 12.04/64. The system uses swraid. It's easy to manually boot from DVD, install/activate RAID, reformat system partitions (/, /boot, /usr, /var) and mount the entire hierarchy for installation under /mnt/target before I fire up the installer. But how do I make the installer skip these operations?


(I'm aware that the default install doesn't support boot from swraid so I have to chroot, install mdadm, then update initrd and grub manually before rebooting at the end of the installation)

---

### Post by dino99 on 2012-05-06
if you choose the "manual" installation setting with the "alternate" iso, then when the installer ask for partitioning, simply go backward, you will get the menu the installer is following. So there select the next option (partitioning+1)

but im seeing that your partitioning is the old fashion (/boot, /var, ...) and is different nowadays of the default partitioning schema (/, /home, /swap only) , yours is still possible, meanly on servers, but with additional custom tweaks to adapt the pathes and symlinks.

---

