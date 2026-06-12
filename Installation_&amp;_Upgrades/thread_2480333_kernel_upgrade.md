---
title: "kernel upgrade"
date: 2022-10-26
forum: Installation &amp; Upgrades
---

### Post by e1ka on 2022-10-26
Ubuntu 22.04.1 LTS

cryptosetup&LUKS for sda1

# /etc/fstab
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
UUID=a83296aa-c855-423f-a399-ad7c4edb5a5f /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap none            swap    sw              0       0
/dev/mmcblk1p1	/media/mmc	vfat	user,owner,utf8,rw,umask=000	0	0
/dev/sda2	/media/windows	ntfs	user,owner,utf8			0	0


white screen with a tiny vertical lines during boot 5.15 kernel
[https://drive.google.com/file/d/1dX95SgFhLY5i4rSYwPbqy5G8XK7TZNaa/view?usp=sharing](https://drive.google.com/file/d/1dX95SgFhLY5i4rSYwPbqy5G8XK7TZNaa/view?usp=sharing)

normal booting with an old 5.10 kernel
[https://drive.google.com/file/d/15zkJrhNf0BfGjs9jIppwbWApAyGwZ08R/view?usp=sharing](https://drive.google.com/file/d/15zkJrhNf0BfGjs9jIppwbWApAyGwZ08R/view?usp=sharing)

I do change initramfs.conf:   COMPRESS=xz  MODULES=dep

---

