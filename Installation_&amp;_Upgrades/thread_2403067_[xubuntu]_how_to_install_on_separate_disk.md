---
title: "[xubuntu] how to install on separate disk"
date: 2018-10-07
forum: Installation &amp; Upgrades
---

### Post by cigero on 2018-10-07
Hi to all,
I need a little help to install xubuntu.
On my laptop I have a primary SSD with Win 7 installed (for university needs) and a HDD (installed with a caddy in the cd-rom slot) with my data. I tried to install xubuntu on a partition on the HDD, creating for 4 partition (/boot, / , /home and swap) and trying to install grub2 both on the SSD and HDD but everytime, after the installation xubuntu starts correctly while on the second restart i can't boot due to grub problem.
Can someone help me and teach me how to correctly install xubuntu?
I'm a noob in linux world and i would to learn, but this problem prevents me.
And also, sorry for my bad english.

---

### Post by yancek on 2018-10-07
Simplify things for yourself and just use a root ( / ) partition and maybe a /home or /data partition.  No need for the other partitions.

Your windows should show as /dev/sda and the external drive as /dev/sdb.  With windows 7, you are using a Legacy/MBR install so install Grub to the MBR of the external drive (sdb?).  You need to verify this.  It would be useful if you posted what the problem/error is with Grub on second boot?

---

