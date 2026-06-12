---
title: "ZFS first install, stuck on boot"
date: 2020-04-29
forum: Installation &amp; Upgrades
---

### Post by Vinencre on 2020-04-29
Hello,

I am not new on Linux, but a total newbie concerning ZFS.

I tried to install Ubuntu 20.04 on an entire drive with NFS, but even if the installation seems to proceed without any problem, at the first boot, I am stuck at the Ubuntu logo spinning.

When looking at the process, the only failure is:
```
[FAILED] Failed to start Load AppArmor profiles.
See 'systemctl status apparmor.service' for details.
```

I followed the default installation, only choosing another language (French), and for the keyboard (French/French).
I tried the first time with normal installation and updates checked. Second time minimal installation and updates unchecked. Same problem.
I tried in ext4, same options, no problem.

It is on a 128 GB SSD in a PC connected via SATA. On a not modern computer with no exotic hardware.

Here are the partitions:
```
partition n° 1 sur SCSI4 (0,0,0) (sdd) de type
- partition #0,0,0p1 en tant que vfat utilisée pour ESP
- partition #0,0,0p5 en tant que swap utilisée pour swap
- partition #0,0,0p6 en tant que zfs utilisée pour bpool
- partition #0,0,0p7 en tant que zfs utilisée pour rpool
```

Is there some prerequisites?

Thanks for your help.

---

### Post by CelticWarrior on 2020-04-29
ZFS is experimental. Expect things not working in some cases. At least you know EXT4 works, as expected.

---

### Post by Vinencre on 2020-04-29
I know, it is written in capital letters.

So if someone could help me find leads to know why, and how to solve it, I would gladly accept it.

---

