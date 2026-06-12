---
title: "Not seeing SATA drive after 8.10 upgrade"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by TrevorDuke on 2008-11-18
Since upgrading to 8.10, my secondary SATA drive is not seen by ubuntu.

I have all OSes and program files, pretty much all the basics on my 160gb SATA primary. However, All downloads, as well as all media (that other machines need) is on my 500. I look in mnt, media, dev, the drive is nowhere to be found. I upgraded straight from 8.04, and whenever it told me to merge config files, i am pretty sure i told them all to replace the previous files, but the fact that it is not seeing a drive is ridiculous.


I am also having the Transmission crash (someone suggested seg fault), but likely because it is trying to access this drive. 

Thanks!

---

### Post by taurus on 2008-11-18
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

---

