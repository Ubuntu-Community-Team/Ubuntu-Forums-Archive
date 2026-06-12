---
title: "PXE Boot network modules - can't open /tmp/net-eth0.conf"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by chipperuga on 2010-10-21
I am getting the following error when booting PXE: can't open /tmp/net-eth0.conf

I was told to add the network driver/module to /etc/initramfs-tools/modules ...but I'm not sure how.

estudiante@pxedust:~$ dmesg | grep 'Ethernet driver'
[    3.217245] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.315536] 8139too Fast Ethernet driver 0.9.28

estudiante@pxedust:~$ /sbin/modprobe -lt net \* | grep '8139'
kernel/drivers/net/8139cp.ko
kernel/drivers/net/8139too.ko

What do I add to the modules file? A line with "8139too.ko"?

---

