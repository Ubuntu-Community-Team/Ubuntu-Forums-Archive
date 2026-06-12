---
title: "Kernel panic on 3.5.0-41-generic"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by whitesmith on 2013-09-27
This morning I was auto-reminded that it was time to upgrade components, one of which was the 3.5.0-41-generic kernel. I did, rebooted, and was rewarded for my efforts by this error: "Kernel panic - not syncing VFS: Unable to mount root file system on unknown block(0,0)." GRUB allowed me to return to the previous (3.5.0-40-generic) kernel, where life is good. But that doesn't solve the mystery--namely, what happened and why. The download came directly from Canonical, which pretty much excludes the possibility of tampering. So what caused the problem in the first place? It isn't free space. This is output from** df -hT | egrep -i "file|^/**":```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       37G  5.4G   30G  16% /
/dev/sdc1      fuseblk   932G  572G  360G  62% /media/Data-SLA360
/dev/sda5      ext4       74G   54G   17G  77% /home
/dev/sdb1      ext4      221G  188M  209G   1% /media/HomeAddition
/dev/sdd1      ext3      917G  856G   15G  99% /media/Bkup-CLA332
/dev/sde1      ext4      917G  278G  594G  32% /media/FreeAgent
```

I'm running 12.04 LTS, 64-bit. There's 32 GB of tested RAM in the box. Any ideas, good folks?

---

### Post by whitesmith on 2013-09-28
Last night I tried:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```No change. Upon reboot I get GRUB's menu, select 3.5.0-41-generic, and then get the selfsame kernel panic. Going back to 3.5.0-40-generic (via GRUB) makes the problem go away, but I wouldn't call this a solution. Anyone in the mood to offer some help to a fellow Ubuntu-er?

---

