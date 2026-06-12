---
title: "Adding disk space to linux"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by josempans on 2011-04-15
Hi everybody, I've recently installed Ubuntu, is my first time with open source system... And I'm really happy with this step... Very surprised.
Now, before trying ubuntu, I've divided my 1TB disk in a few partitions:
80GB for XP
600GB for Data
80GB for Ubuntu
and 120GB for a future Windows 7 installation (so is a NTFS file system) ... Now, the thing is... after started using ubuntu (and solving a lot of new issues, like 3G modems) I don't want windows anymore... unfortunately I can't uninstall XP for one software, pMG Messiah Studio. Anyway, this last 120GB partition, I want to give it to Ubuntu, and using a file system that Ubuntu likes, I think is ext4 (or ext3)... I really don't know. How can this be done? I've already run the disk utility and read the options... but for example: for the file system I can choose a lot, but I don't find ext4 or something like that. Other thing is that I would like Ubuntu use this disk for new soft installations too, can I add the 120gb to the 80gb partition?
I don't want any data loss, so I want to be sure about the steps to make.

Thanks a lot in advance... and have to say again, Ubuntu is very very nice (really, I'm very happy and surprised... I've imagined the linux world writing and writing in the terminal, but is not very far to write and write in cmd, haha)

---

### Post by lmarmisa on 2011-04-15
Welcome to the Forums.

First to give you any recommendation, it would be useful to know more details about your partitions. Please, open a terminal, type this command and give us the result:

```

sudo fdisk -l

```

---

### Post by josempans on 2011-04-15
this is the list given by fdisk (in spanish):

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       95612   686079922+   7  HPFS/NTFS
/dev/sda3           95613      110910   122881185    7  HPFS/NTFS
/dev/sda4          110911      121602    85876737    5  Extendida
/dev/sda5          110911      121161    82336768   83  Linux
/dev/sda6          121161      121602     3538944   82  Linux swap / Solaris

---

### Post by lmarmisa on 2011-04-15
Thanks for your answer. The 120 Gbytes partition is identified by Ubuntu as /dev/sda3.

I do not know what you prefer to do. You have several options:

1) Remove the 120 Gbytes NTFS partition and enlarge the 600 Gbytes NTFS partition with the space of the deleted partition. This is not difficult.

2) Format the partition /dev/sda3 with a Linux filesystem like ext4. This is also simple.

3) Remove the 120 Gbytes partition and enlarge the Linux and extended partition with that free space. This is a little bit more difficult task.

The basic tool you have to use is Gparted. You can install it typing this command:

```

sudo apt-get install gparted

```

---

### Post by josempans on 2011-04-16
well, I would like to do the option 3), but if this is kinda risky then I will choose the 2nd option. Is this gpart soft like the Disk utility in system menu?

---

### Post by Rubi1200 on 2011-04-16
I have 2 recommendations before you start playing with partitions:

1. backups, backups, backups (there is always a certain amount of risk involved with changing/moving/resizing partitions)

2. I suggest you use a LiveCD/USB to do the work; a) GParted is already installed on it by default and b) it is safer since the partitions won't be mounted (you may need to turn the swap partition off right-click > Swapoff)

---

