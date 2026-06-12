---
title: "Grub problems, fresh install"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by TerabyteUK on 2008-10-01
Hi, I've just installed ubuntnu 8.04
This usually goes swimmingly well...

Only ths time, when I reboot, I get ERROR 22, from grub.

My setup

1 physical disk with 4 partitions on it.

1 Vista (works, usually accessible)
2 Ubuntu  sdc7  - hd(2,6)
3 swap
4 xp (works but unaccessible)

I need to dual boot vista with ubuntu.

How can I retrieve both vista and ubuntu to be bootable?

I am running the live disk at the moment.

Thanks

---

### Post by Pumalite on 2008-10-01
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
You might need to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-10-01
Do you get the Grub error 22 before you get a Grub menu, or after you get the Grub menu and select an OS to boot? Also, if you only have one physical HDD, you shouldn't have an "sdc7" as sdc would be your 3rd HDD. Boot your Ubuntu Live CD, open a terminal (applications > accessories > terminal), and please post the following:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```

---

