---
title: "Partition sizes"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by eFFeeMMe on 2007-12-02
Hello, I need help partitioning my hard drive.

I don't plan on dual booting, I only want to install Ubuntu properly with any partition I might need(like /boot, /home, or others, I don't know).
I have 160GB of space. It would be great if you could tell me what the different partitions are for and how much space would be typically needed for each.

Thanks in advance :)

---

### Post by monktbd on 2007-12-02
well putting /home on an extra partition is clear and as you surely know it holds your (and other users) personal data.

/usr holds the programs you install as root/sudo so you might want to have that an extra partition although a / big enough holding the programs is most often enough.
if you ever run out of space on / you can always make another partition for /usr and/or /usr/local and copy all contents there and point ubuntu to use the new partition as /usr or /usr/local respectively.

if you plan to do some webdevelopment/database work on your comp then you might want to put /var on a seperate partition to be better able to check the space there. also it saves you from maybe flilling up / if there ever goes something wrong you dont notice and the logs in /var/log  get so huge to use up all the space on /.

/etc holds all the system wide configurations, usually quite small and not really needed to put on an extra partition.

/boot on an extra partition makes sense especially when you plan to use several distributions and start them easily from one grub install.

i used to have a lot of partitions but i kinda changed that to have just / and /home plus some special /data folders that use fat32 on seperate partitions.

if you are not sure right now how to set it all up and don't need all your harddisk space right away then leave some unpartitioned to use for later when you know where you are short of space. you can use the remaining space anywhere on your system, even as a subfolder like /home/youruser/Documents etc...

---

### Post by eFFeeMMe on 2007-12-02
Thanks a lot for your help, everything's clear now!

EDIT: uhm, how big should /boot be usually?

---

### Post by monktbd on 2007-12-02
my old dapper install with a lot of kernel updates has a /boot folder with the size of around 55MB. so i guess with 500MB you are very much on the safe side.

one thing i forgot in the above post is that /tmp is often used for burning dvds or cds as the temp location and you might need that free space to properly burn the discs. that can be quite a bit of space for dvds but the location of the temp files  is often configurable within the burning program as well.

---

