---
title: "Intermittant failure to boot: apparent erratic behaviour"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Ubu_user_101 on 2012-05-15
Hi,

I installed 11.10 some time ago. While I was amazed at how simple it was to install ubuntu I have had problems in that, Ubuntu more often than not will fail to boot properly.

I typically have to turn my PC and off several time before reaching the ubuntu login page. Most often the machine will wait for my response on the grub page. When I select ubuntu then it may or may not boot.

There seems to be no pattern or logic to indicate when it will boot sucessfully. I do find it amazing a computer can appear to have such erratic behaviour. 

Can anyone advise on how I might begin to solve such a weird problem?

Thanks

---

### Post by wilee-nilee on 2012-05-15
Update the grub.cfg file periodically by running 

```
sudo update-grub
```

Check the fstab file and look if the UUID is correct for the partitions.

This is the command to show the UUID for each partition.

```
sudo blkid
```

This is the command to open fstab.

```
sudo gedit /etc/fstab
```

Just maintenance stuff really hard to say the exact cause, when it happens hit the arrow up key to see the error and post it.

---

