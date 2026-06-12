---
title: "How to clone Ubuntu onto another machines?"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by vadimc on 2006-05-16
Hi.

I have a machine with installed and configured Ubuntu. I have another 2 machines and I would like to clone installation from the first one. All machines have specific NIC cards which are not supported by Ubuntu (I had to install specific NIC driver onto the first system).

Thanks in advance.

---

### Post by NoUse on 2006-05-16
If you can get both disks into one machine, gparted can copy partitions.  Just copy the / partition from one machine on to the second machine, make sure to create a swap partition as well.

Then you will probaby have to re-run grub setup on the second machine for it to boot properly.

These intructions might help: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

I've never done this but this would be the way I would try it.

---

### Post by aysiu on 2006-05-16
PartImage

---

