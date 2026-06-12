---
title: "Gutsy installation help, dual OS"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by nukemelamers on 2008-03-24
the threads i look up doesn't resolve my problem,

i got 160GB, partitioned ,C: Vista Pre-installed ,D: for data<
i've make new partition by shrinked D, and E: appear(10GB) (special prepared for ubuntu)

I downloaded ubuntu and burn it to CD, and......
now lets skip, when i install ubuntu 7.10, at the partition stage,
what should i choose,??
-I want to keep my vista on C, and without delete my D, and install ubuntu on E?
I look up on google and those tutorial doesn't make me sure..

i really want to try ubuntu, coz vista getting boring but i still want to keep it :lolflag: (sorry bad english:KS)
-------Can't wait to try ubuntu-------:guitar:

---

### Post by Pumalite on 2008-03-24
From your Live CD's Terminal, post:
sudo fdik -lu

---

### Post by nukemelamers on 2008-03-24
> **Pumalite said:**
> From your Live CD's Terminal, post:
sudo fdik -lu

what is that mean??
(sorry i'm too newbie for dual os)

---

### Post by Pumalite on 2008-03-24
Boot your Ubuntu Live CD. Go to Applications>Accessories>Terminal. Copy and paste my command at the Terminal. Press 'Enter'. Copy and paste the result here.

---

### Post by nukemelamers on 2008-03-24
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1729cee0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  27  Unknown
/dev/sda2   *    20467712   166793215    73162752    6  FAT16
/dev/sda3       166793216   295985143    64595964    7  HPFS/NTFS
/dev/sda4       295985152   312578047     8296448    f  W95 Ext'd (LBA)
/dev/sda5       295987200   312578047     8295424    7  HPFS/NTFS

Disk /dev/sdb: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders, total 8058880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d80a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     8058879     4029424    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

I tried to install on the drive i want, but it says something, about the root..

---

### Post by Pumalite on 2008-03-24
Explain the details of what you did to me.

---

### Post by nukemelamers on 2008-03-24
> **Pumalite said:**
> Explain the details of what you did to me.

you told me to type sudo fdik -lu, but nothing appear, i tried to type sudo fdisk -lu thats appear...

I am using installer from CD,
then when it comes to the partition stage --3 option- i choose manual--, i choose the drive(already partitioned) then it says 
but, now just tell  me how to install on the E: without deleting any data on C and D, 
i'm really confuse

---

### Post by Pumalite on 2008-03-24
You are going to figure out which one is 'E' out of the fdisk. When you go 'Manual', do a first partition for the filesystem with mount point '/' (you just have to plant an / in the blank space assigned to designate 'mount point')(format: ext3)

---

### Post by nukemelamers on 2008-03-24
@Pumalite
before i check ur last post, i already installing ubuntu with any hope, but......
no data were deleted, 
ubuntu 7.10 successfully installed :guitar::guitar::guitar: YEAH!!!!!!!!........

thanks for your help....



[B]
THREAD CLOSED[/B]

---

