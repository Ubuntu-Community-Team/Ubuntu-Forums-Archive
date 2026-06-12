---
title: "No recommended repair option in boot repair"
date: 2021-02-23
forum: Installation &amp; Upgrades
---

### Post by ronnie36 on 2021-02-23
I have installed Ubuntu in my laptop but i can't see the GRUB bootloader. While trying to repair GRUB, there is no recommended repair option in boot repair.
Here is my Boot Info summary- [https://paste.ubuntu.com/p/tChvMJ8JpX/](https://paste.ubuntu.com/p/tChvMJ8JpX/)

---

### Post by oldfred on 2021-02-23
Is drive still in Intel RST? It should be AHCI.
It looked like it is trying to mount partitions with the RAID driver (mdadm) and failing.

Also make sure Windows fast start up is off as that sets hibernation flag and prevents Linux NTFS driver from seeing the NTFS partitions. Windows updates will turn fast start up back on also, so if issues seeing NTFS from Ubuntu turn it off again.

RST info & Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

---

