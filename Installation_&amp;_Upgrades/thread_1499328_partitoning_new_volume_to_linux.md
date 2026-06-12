---
title: "partitoning new volume to linux"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by evilwonka on 2010-06-01
i whipped out windows and now I'm trying to figure out on how to add my old windows partition to my Linux partition? i don't want to reinstall Linux and lose my stuff please help me

---

### Post by elespejo on 2010-06-01
Get a live cd/usb distro and use gparted to expand the existing linux partitions.

---

### Post by evilwonka on 2010-06-01
i want to use all the existing unused partition and put it to Linux 10.4

---

### Post by pastalavista on 2010-06-01
If you're in Linux now, just install 'gparted' partition manager from the software center and format the partition to ext3 or ext4 format and you'll be able to use it as a seperate partition. No need to change the partition you're using now.

---

### Post by evilwonka on 2010-06-01
Thanks guys i did'int think of that. sometime you just have to ask the right people :D

---

### Post by pastalavista on 2010-06-01
> **evilwonka said:**
> Thanks guys i didnt think of that. sometime you just have to ask the right people :DI forgot. 10.04 has a disk tool already installed. In the System-->Administration menu "Disk Utility" runs an application called 'palimpsest' which can also be run from Alt+F2 or Terminal (with gksu) which can format the drive too. Be careful, it's a powerful tool.

---

### Post by evilwonka on 2010-06-01
Well i did that and now it says unknown?

---

### Post by evilwonka on 2010-06-02
OK it worked thanks a lot

---

### Post by evilwonka on 2010-06-02
is it better to have to partitions then it is one big one, and if it is why?

---

### Post by dino99 on 2010-06-02
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

