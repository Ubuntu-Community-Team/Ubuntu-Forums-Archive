---
title: "ubuntu alternative server cannot install to partitions"
date: 2019-04-07
forum: Installation &amp; Upgrades
---

### Post by ruwan2 on 2019-04-07
Hi, Everyone:

I have a dual boot Dell desktop computer. The Ubuntu is 16.04LTS now. I'd like to install the latest 18.04 "Alternative server edition" for Nvidia card support reason, but I cannot find the options to utilize the already partition in the installation process. It can only install to the entire drive partition option, or to create new partitions in the process. My dual boot drives has Windows 10 and Ubuntu two OS. I have to install new Ubuntu to the existing partitions. I'd like to have a new installation, because an OS upgrade doesn't work with Nvidia card. 

Do you know how to make Ubuntu alternative server install on a few already partitions?



Thanks,

---

### Post by houstonbofh on 2019-04-07
Are you wanting to install, or upgrade an existing install?  The partitions are different because 18 uses a swap file as opposed to a swap partition like in 16.

---

### Post by ruwan2 on 2019-04-13
I want to install 18.04 to overwrite 16.04. If 18.04 doesn't use swap partition, that is OK. I can convert the old swap partition of 16.04 for other use, or to delete it first, then a neighbor partition absorb it.
My question can be reorganized as: Does HWE 18.04 support manual partition?

Thanks,

---

### Post by Dennis N on 2019-04-13
> My question can be reorganized as: Does HWE 18.04 support manual partition?
It will use the same installer as the other releases, so manual partitioning is supported. If there is a swap partition detected when installed, it will be used instead of a swap file.

---

