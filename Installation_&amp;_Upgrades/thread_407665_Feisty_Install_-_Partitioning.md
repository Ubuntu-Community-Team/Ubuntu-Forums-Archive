---
title: "Feisty Install - Partitioning"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by litwell on 2007-04-12
Hi

I did a clean install from Ubuntu Feisty Alternate CD.

After logging in, I could not update my system correctly.
Somehow the "/" root partition was full ! :shock:

You can see the partitioning scheme used at the bottom.(*)

The Disk Usage GUI utility was not very helpful... So, I ran:

```
litwell@A8JS:/$ sudo du -shc /*
Password:
5,4M    /bin
10M     /boot
0       /cdrom
392K    /dev
7,7M    /etc
11M     /home
0       /initrd
0       /initrd.img
146M    /lib
0       /lib64
0       /media
0       /mnt
0       /opt
0       /proc
32K     /root
6,9M    /sbin
0       /srv
0       /sys
20K     /tmp
1,7G    /usr
356M    /var
0       /vmlinuz
2,2G    total
```
... and...
```
litwell@A8JS:/$ sudo du -shc --apparent-size /*
5,2M    /bin
10M     /boot
11      /cdrom
186K    /dev
4,7M    /etc
9,7M    /home
6       /initrd
33      /initrd.img
141M    /lib
4       /lib64
183     /media
6       /mnt
40      /opt
2,0G    /proc
11K     /root
6,6M    /sbin
6       /srv
314M    /sys
9,4K    /tmp
1,5G    /usr
339M    /var
30      /vmlinuz
4,3G    total
```
Is this difference in "/proc size" due to how hibernation / suspend to disk is configured?

I could not find anything regarding the subject. It would be nice to have some info.
Any advice is very welcome :D

Is it possible to configure a partition for hibernation data?
or
Should I just make bigger "/" root next time?


(*)I use a simple disk partitioning and so far I've never had trouble.
Here's a little summary:

**/boot** - **100MB**  -  Grub, Kernels, etc.
**/ ** -  **250MB** - Ubuntu's root. (Normaly, this size for "/" is generaly enough to make backups of "/etc")
**/usr ** - ** 5GB**
**/opt**  - ** 2GB**
**/var ** -  **3GB** - (Probably a gentoo habit :P)
/home  -  20GB
**/tmp ** -  **4.7**GB - (Some GUI apps use /tmp for file transfers. This size is enough for dvd backups, etc.)
**SWAP**  -  **2GB** - (I have 2GB RAM but I don't follow the "2x RAM" rule.)

---

### Post by litwell on 2007-04-12
Update.

Made a clean re-install, this time with a root "/" partition larger than 3GB.

Still can't use the system. It tells me that "/" is full.

I also noticed a strange thing. There are two winxp partitions mounted on /media (I left default location from install).

DU gui reported that  /media folder was almost 90% full. I know that in reality it has about 12GB used out of 15GB + 20GB (two ntfs partitions mounted there). :roll:

Unmounted everything on /media, refreshed DU gui.
This time it reported /usr was 75% full. It should not... Standard install gets you about 1,5 GB (see my previous post). In a 5GB partition, this should be the other way arround (75% free :P).

I can't use Feisty Fawn and I don't like the idea of having one big fat partition.

---

### Post by godvalve on 2007-04-12
I also had a little trouble with partitioning in Feisty. I didn't have the same troubles as above, but I did have trouble getting my head around how the partitioning tool worked. I much prefer to have a visual representation of my partition tables as is available under 'gparted' used in Edgy. I was eventually able to get my install through.

---

### Post by bulldog on 2007-04-12
Why don't you make just a 10GB / partition and a separate /home partition.
A little swap partition to make it look nice and your clear for take off.

---

