---
title: "install freebsd,windows xp,ubuntu"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by Ramakrishna1 on 2012-09-02
how to install freebsd 8.3,windows xp and ubuntu 12.04 in my laptop?
my laptop hard disk consists of one primary partition and one extended partition.
the extended partition consists of five logical drives.
then how to install freebsd 8.3,windows xp and ubuntu 12.04 in my laptop?

---

### Post by Ramakrishna1 on 2012-09-02
any body help me plz......

---

### Post by Laiquendi on 2012-09-02
Just... install it ^^ one by one, try not to overwrite first by the second and third (while choosing partitions). I would suggest installing Windows first, becaue window's bootloader won't find other systems.

---

### Post by Ramakrishna1 on 2012-09-02
> **Laiquendi said:**
> Just... install it ^^ one by one, try not to overwrite first by the second and third (while choosing partitions). I would suggest installing Windows first, becaue window's bootloader won't find other systems.

my question is can i install two operating systems in two different logical drives of one extended partition

---

### Post by oldfred on 2012-09-04
Windows has to have a primary partition. A second install of Windows can be in a logical, but then you cannot delete the first as the second moves all its boot files to the first install.

Not sure about freebsd, but I thought it needed a primary partition also. Someone posted that it was best on a separate drive as it does not play nice with other systems, but that was a couple of years ago.

I have many Linux installs in logical partitions.

---

