---
title: "[SOLVED] Installing from the minimal CD image within an existing Ubuntu partition"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by absolutezero1287 on 2008-06-19
I'd like to install the contents of the minimal CD image (Ubuntu 8.04) onto a seperate partition from within my existing Ubuntu system. The reason being that the cd won't detect my wireless internet. These are the steps that I've taken.

```

leonardo@desktop:~$ sudo -s


root@desktop:~# mkdir /mnt/Ubuntu_minimal

root@desktop:~# MIN=/mnt/Ubuntu_minimal


root@desktop:~# echo $MIN

/mnt/Ubuntu_minimal


root@desktop:~# mount -t ext3 /dev/sda3 $MIN


root@desktop:~# cd  ~/Desktop

root@desktop:~/Desktop# mv Ubuntu_mini.iso $MIN


root@desktop:~/Desktop# cd $MIN


root@desktop:/mnt/Ubuntu_minimal# mkdir mnt


root@desktop:/mnt/Ubuntu_minimal# mount -o loop Ubuntu_mini.iso mnt


root@desktop:/mnt/Ubuntu_minimal# mkdir extract-cd


root@desktop:/mnt/Ubuntu_minimal# rsync -a mnt/ extract-cd


```

I now have the contents of the install CD in /dev/sda3 with my primary partition being /dev/sda1. How do I set everything up? Where do I go from here?

---

### Post by absolutezero1287 on 2008-06-19
Bump. Please help, anyone.

---

### Post by avtolle on 2008-06-19
Take a look at [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) for some beginning steps.

---

### Post by absolutezero1287 on 2008-06-20
That didn't really help. I can't use the CD because it requires an internet connection. Would it be possible to use debootstrap to install the minimal CD image in a seperate partition?

---

### Post by absolutezero1287 on 2008-07-04
I used debootstrap and succesfully made a minimal install. I would say that this thread is solved but it really isn't

---

