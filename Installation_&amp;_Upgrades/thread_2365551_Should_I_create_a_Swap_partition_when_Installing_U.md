---
title: "Should I create a Swap partition when Installing Ubuntu 1 7.04"
date: 2017-07-07
forum: Installation &amp; Upgrades
---

### Post by automate-stuff on 2017-07-07
I have heard that fresh installation of 17.04 does not need a swap partition...it creates a swap file when you are installing it....Is this true ? Should I create a swap partition during the installation ? what do you recommend, Swap partition or Swap file ? if you recommend swap partition, what should be the size on a 250GB NVMe SSD with 16GB of RAM ?

---

### Post by deadflowr on 2017-07-07
Do nothing and take the swap file that the installer makes for you as is.
> 
if you recommend swap partition, what should be the size on a 250GB NVMe SSD with 16GB of RAM ?
That depends.
If hibernating, then make it equal to ram.
If just to have a swap partition, then literally any size is fine;
Probably 1 GB would be well more than you'd ever need, anyway.

Also depends on what you plan on running on the system.
(The more apps you get going and the hungrier those apps are would mean the possible need to have a larger swap size.)

---

### Post by automate-stuff on 2017-07-07
So when installing, I always choose the "something else" option...because I want to manually create the partition and also save the boot-loader on the device that I like...so you are saying I shouldn't create a swap partition when I choose the "something else" option and go to the partitioning step , With no swap partition created, I shall proceed to install the 17.04 and the installer will make the swap file automatically...Correct ?

Also I almost never hibernate....I usually put the Laptop to sleep all the time after any session....I also run a lot of apps...maybe 40-50 open windows...Chromium, Different IDEs, Evince etc ... given these facts...do you recommend me to install a swap partition or don't touch anything and let the installer install the swap file by default ?

---

### Post by efflandt on 2017-07-08
With 16 GB RAM and SSD I would not even create a swap partition or file unless it is a laptop that you want to be able to hibernate (if battery goes low). And then you would want to look into **swappiness** setting for minimal swapping to save write wear on the SSD. And I use tmpfs for /tmp (similar to what live/install does in /etc/fstab), since /tmp is erased every boot anyway. But I don't know how much RAM those 40-50 windows you would have open would use.

I didn't even have swap when first installing Ubuntu on my mechanical hd because Dell was using 3 msdos partitions and I did not know if grub could be installed in an extended partition instead of the mbr. Also initially some Win7 programs would store some data in what they "thought" was an unused part of the mbr, overwriting part of grub2 which was larger, and occasionally some Win7 updates would fail if using grub instead of its mbr. So I just made sda4 /, installed grub to that instead of mbr, set the boot flag to sda4, and in the rare case that a Win7 update fails, I can switch the boot flag for Win7 to reboot itself using its own standard mbr. I am currently booting 16.10 from 512 GB mSATA SSD card (from failed laptop) in SATA adapter (sdb) and put its grub in the mbr of sdb (no swap). I just recently upgraded RAM from 8 GB to 16 GB and actually use more than 8 GB RAM now, but a vast majority is reusable automatic drive cache. An SSD can boot my PC about as fast as it can wake from suspend, so I do not use suspend or know if booting from hibernation would be faster.

---

### Post by Bucky Ball on 2017-07-08
You should create a /swap partition during 'Something Else'. It is a default selection in the drop-down menus. Just create a 2Gb partition and then select the type as 'swap-space' or 'linux-swap' (can't remember exactly what the default name is). That is it.

You create the /swap during manual partitioning just as you would create any other partition. It is making it 'swap-space' the only diff.

---

### Post by kurt18947 on 2017-07-09
My systems are pre UEFI and are limited to 4 partitions. I use a swap file rather than a swap partition to save a partition. I don't use hibernation which is the only thing that requires a physical swap partition AFAIK.

---

