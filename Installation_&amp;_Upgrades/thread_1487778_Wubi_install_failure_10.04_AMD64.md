---
title: "Wubi install failure 10.04 AMD64"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by hebbal1273 on 2010-05-19
I am unable to install Ubuntu 10.04 on my windows XP SP3 laptop using wubi. The laptop is HP NX6325. I am trying to install amd64 bit version. My previous 9.10 64 bit was installed flawless. The iso file is copied into the same directory as wubi. After the initial preparation wubi asks to reboot. After I reboot I get the Windows & Ubuntu option. After selecting Ubuntu it goes into the grub command prompt.
My 320GB HD is partitioned as follows C:(Windows XP SP3, 120GB) D:(windows recovery partition 7GB) & F:(170GB) I am trying to install Ubuntu into F:

---

### Post by hebbal1273 on 2010-05-21
Any solutions? From googling what I saw is that grub is having a problem with accessing extended partitions. If I do ls it lists the above F: as hd(0,5) as unknown partition. It is formatted as NTFS. lsmod lists the ext2 module loaded properly

---

### Post by Toto Leung on 2010-06-04
[http://ubuntuforums.org/showthread.php?p=9409336&posted=1#post9409336](http://ubuntuforums.org/showthread.php?p=9409336&posted=1#post9409336)
Same problem in Windows 7...

---

