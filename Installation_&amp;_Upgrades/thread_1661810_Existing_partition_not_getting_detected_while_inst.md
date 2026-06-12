---
title: "Existing partition not getting detected while installing Ubuntu 10.10"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by naveen_kar on 2011-01-07
Hi,

My Laptop is Dell Inspiron 1525 with Dual boot Windows vista as well as Linux mint. I was trying to install Ubuntu over Linux Mint, but it is not detecting the existing partitions asking me to go ahead and edit the partitions manually (which I am not familiar with). Earlier when I was installing Linux Mint or SUSE, it was detecting the existing partitions and could install easily. Currently I am sure how to go about, but I would like to install Ubuntu badly.
Please help.

Thanks
Naveen

---

### Post by sikander3786 on 2011-01-07
Welcome to the forums :-)

The installer has changed a bit.

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
courtesy of forum member *kansasnoob*

You might need to partition manually. Or if you are unsure, post the output of this command.

Applications > Accessories > Terminal:

```
sudo fdisk -lu
```

---

