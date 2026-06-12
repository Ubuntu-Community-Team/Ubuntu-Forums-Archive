---
title: "Forgot to Install Boot Loader, Help!"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by johansur on 2008-08-28
I installed ubuntu 8.04(hardy) when have to choose "install boot loader" i din't tick it. So, when it complete and restart. It can't get in ubuntu, and only in dos mode:

Form here

    [Minimal BASH-like editing is supported. For the first word, TAB list possible command completions. Any ware else TAB lists the possible completions of device/filename. ]

grup> 

End here

Could you help me how to install boot loader from there.

---

### Post by cariboo on 2008-08-29
Use your livecd to install grub, bootup to the desktop then:

```
sudo mount /dev/sda1 /mnt
```

substitute /dev/sda1 for the partitioo you have ubuntu installed on, then

```
sudo chroot /mnt
```

next

```
sudo apt-get install grub
```

Jim

---

### Post by tuxerman on 2008-08-29
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

