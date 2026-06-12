---
title: "Reinstallation of Windows 7 which is dual booted with Ubuntu"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by trancephorm on 2010-12-24
So I have working dual-boot configuration with Grub (installed Ubuntu as the 2nd system). Now I just want to reinstall Windows 7 on its partition. What is the safest way to do this?

---

### Post by Quackers on 2010-12-24
Do you have a Win 7 installation disc? That would be best.
If you try re-installing from a set of recovery dvd's or from a recovery partition it may insist on using the whole disc.

---

### Post by trancephorm on 2010-12-24
Sure I have it, but I assume Windows 7 will mess the booting process, so I'm asking.

---

### Post by Quackers on 2010-12-24
Yes, any re-install of Windows will re-write the mbr and mess up the Ubuntu boot process. It would be necessary to re-install Grub2 to the mbr after.

---

### Post by trancephorm on 2010-12-24
OK, so I guess [this](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) is where the needed document is residing?

---

### Post by Quackers on 2010-12-24
Normally it would be done by booting from the Live cd/usb and opening a terminal and entering
```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```
Where sdXY in the first command is your Ubuntu root partition (eg sda5) and sdX in the second command is the disc designation (eg if sda5 is in the first command then sda would be in the second command)
Note no partition number in the second command!

---

### Post by kansasnoob on 2010-12-24
> **trancephorm said:**
> So I have working dual-boot configuration with Grub (installed Ubuntu as the 2nd system). Now I just want to reinstall Windows 7 on its partition. What is the safest way to do this?

Actually we should know what the current partition arrangement is so, if you've not begun yet, please post the output of:

```
sudo parted -l
```

---

### Post by trancephorm on 2010-12-28
Thank guys, it works ok!

---

