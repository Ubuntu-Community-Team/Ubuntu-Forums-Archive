---
title: "blank screen + flashing curser w/ Maverick (not Natty)"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by jeliocranch on 2011-08-29
[SIZE=2]bit convoluted situation: 
re-installing Maverick after trying out several other flavors of linux.  I have a separate home partition remaining from previous installs.  Also, I want to install grub2 to its own partition, so its "easy" to add and subtract OS's.

Live CD for 10.10 64bit, Here are my partitions

sda1: /boot (Ext2)
sda2 (extended)
  sda5: swap
  sda6: /  maverick (Ext4)
sda3: /home (Ext4)

Once I reboot, I get blank screen with a flashing cursor.  I saw a tutorial about that with Natty, using Grub 1.99, but I think Maverick uses 1.98, and I understand its different with regards to this.

I notice from prior installs, my /home has /boot in it, but checking sda1, all the boot files seem to be there.
[/SIZE]

---

