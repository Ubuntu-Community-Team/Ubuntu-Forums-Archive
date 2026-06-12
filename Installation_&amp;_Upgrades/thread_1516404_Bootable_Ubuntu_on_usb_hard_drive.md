---
title: "Bootable Ubuntu on usb hard drive"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Lord Snow on 2010-06-23
Hi i am trying to install ubuntu 10.04 on my 1 tb my passport drive and am having loads of trouble. i am unsure how to format the frees space for the boot loader and main drive. Also what partitions are specific for ubuntu to function. This drive is formatted with masterboot partition and contains two other partitions for media and backup. The computer it will be mainly used on is a macbook pro with refit installed on it.

---

### Post by wilee-nilee on 2010-06-23
> **Lord Snow said:**
> Hi i am trying to install ubuntu 10.04 on my 1 tb my passport drive and am having loads of trouble. i am unsure how to format the frees space for the boot loader and main drive. Also what partitions are specific for ubuntu to function. This drive is formatted with masterboot partition and contains two other partitions for media and backup. The computer it will be mainly used on is a macbook pro with refit installed on it.

I would ask the mods to put your thread in the apple part of the forums that might help.

---

### Post by C.S.Cameron on 2010-06-23
When you get to formatting select Specify partitions manually (advanced). 
You should have the option to keep the media and backup partitions and add or change partitions. Make a ext4 partition with mount point "/" and then provide swap space.
You will see a colour bar showing the partitions.
You will still have the option to quit without changing things.

---

