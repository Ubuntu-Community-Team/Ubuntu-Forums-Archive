---
title: "Can't upgrade from 10.10 to 11.04 a3"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by toolbox1234 on 2011-03-10
I have ubuntu 10.10 on my laptop dual boot with win 7. When I try to upgrade to 11.04 a3 from DVD, it complains about it can't unmount /dev/sda2 (the partition where my 10.10 is located). Why would /dev/sda2 is mounted when I start from DVD?

---

### Post by Kirboosy on 2011-03-10
Maybe the fstab is set to auto mount ext3/4 partitions. What happens if you type in a terminal ```
sudo umount /dev/sda2
```Also are you sure you want to upgrade to 11.04? Its still highly buggy...


~Caboose

---

