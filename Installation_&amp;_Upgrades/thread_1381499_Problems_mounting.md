---
title: "Problems mounting"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by joomafoo on 2010-01-14
I had installed my second hard drive and had it automatically mounting on loggin.. All was well untilol i accidentally unmounted the hdd instead of ejecting a dvd and spent the rest of the night getting the drive to mount again my fstab file no longer matched the directory so i changed it and got the drive to mount finally..When i booted up my computer today the drive did not mount so i went into the terminal to mount it and it tells me only root can do so, so i sudo the command and get this msg 
"mount: /dev/sdb1 already mounted or /media/westdig busy" can anyone help me get my drive up n kickin as all my media is on it?
thx joo

---

### Post by dstew on 2010-01-15
It would be good to know just what is mounted where at the time you get this error. We can figure it out by looking at the output of these commands:```
sudo fdisk -l
cat /etc/fstab
cat /etc/mtab
```If there is actually something mounted on /media/westdig, you can probably figure that out if you look at its root directory:```
ls -l /media/westdig
```

---

