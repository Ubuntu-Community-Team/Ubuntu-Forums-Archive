---
title: "Installation Help Please"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by Mike162 on 2010-10-30
Hello,

I have a dual boot machine  XP/Vista.

Both Windows O/S are on one 150GB  HDD with two partitions (C & D drives) - one O/S to each partition.

A second HDD (E drive) - 160GB - has data only, and around 80GB free space.

Ubuntu is working fine live from the DVD.

1.   Would I best install Ubuntu on the E drive without attempting to mess with existing partitions or create new partitions?

2.   Where would I install the boot loader? I want to make sure that when I boot the machine I am offered the option of all of the 3 O/S

3.   This is very new to me. Are there any particular pitfalls here or anything that I should know?

Thanks

---

### Post by mikewhatever on 2010-10-30
1. It doesn't matter. Since the E drive is formatted and contains data, you'll have to mess with partitions anyway.

2. It depends. If you know you want to keep Ubuntu, the MBR or the first hdd should do. If not, you might want to install it to the Ubuntu partition and use [EasyBCD]("http://neosmart.net/dl.php?id=1") to reconfigure the Windows bootloader so that it also points to Ubuntu.

3. Partitioning and bootloaders are tricky for some.

---

### Post by Mike162 on 2010-10-30
Thanks for that, however I would be grateful if I could have an "idiots guide"/specific recommendations.

I do intend to use Ubuntu as well as Windows on my pc.

---

### Post by mikewhatever on 2010-10-30
Recommendations for what, installing, partitioning, bootloaders?
If you've never ever installed an OS or partitioned an hdd, I'd suggest downloading VirtualBox and practicing.

---

