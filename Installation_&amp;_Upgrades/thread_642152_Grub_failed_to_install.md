---
title: "Grub failed to install"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by BenjaminW on 2007-12-16
Hey there, thanks in advance for the help. I am trying to install Ubuntu on my girlfriend's laptop, which was split into 2 partitions. I wanted to install Ubuntu on one partition, so we backed everything up, formated one partition to ext3, and didn't create a swap partition because I was going to create a swap file later. It gets to 93%, and then told me Grub failed to install and this was a critical error. In look at that partition, it looks like Ubuntu installed, it's just that grub didn't. I am going to try wiping the partition again and reinstalling, but if that doesn't work, does anyone have any suggestions?

---

### Post by Pumalite on 2007-12-16
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Pumalite on 2007-12-16
Could also be a bad burn.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by LinuxGuy1234 on 2007-12-16
> **BenjaminW said:**
> Hey there, thanks in advance for the help. I am trying to install Ubuntu on my girlfriend's laptop, which was split into 2 partitions. I wanted to install Ubuntu on one partition, so we backed everything up, formated one partition to ext3, and didn't create a swap partition because I was going to create a swap file later. It gets to 93%, and then told me Grub failed to install and this was a critical error. In look at that partition, it looks like Ubuntu installed, it's just that grub didn't. I am going to try wiping the partition again and reinstalling, but if that doesn't work, does anyone have any suggestions?

In the partition (just a chroot is fine), try installing LILO and running /sbin/lilo.

---

