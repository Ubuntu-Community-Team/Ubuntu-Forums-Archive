---
title: "uninstall 12.04 after installing 14.04"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by kirkcudbright on 2014-08-03
i wish to install 14.04 but to install as duel boot with my existing 12.04 for a trial period.
will i be able to then uninstall 12.04 without loosing any apps and files

---

### Post by ajgreeny on 2014-08-03
The simple answer is, yes, it is possible to do it.
How easy that will be depends on your current partition layout.
Do you have a separate /home partition? Let's see the output of **sudo fdisk -l** in terminal please.

---

### Post by kirkcudbright on 2014-08-03
hi
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000960e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   159807487    79902720   83  Linux
/dev/sda2       159809534   160835583      513025    5  Extended
/dev/sda5       159809536   160835583      513024   82  Linux swap / Solaris
root@terry-desktop:/home/terry2# 


is that ok

terry

---

### Post by kansasnoob on 2014-08-03
Also post the output of:

```
df -H
```

and:

```
free -m
```

---

### Post by kirkcudbright on 2014-08-03
terry2@terry-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        76G   39G   33G  54% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           375M  1.2M  374M   1% /run
none            5.0M  8.0K  5.0M   1% /run/lock
none            1.9G  300K  1.9G   1% /run/shm
/dev/sdc1        30G   12G   18G  39% /media/linuxback
terry2@terry-desktop:~$ 


terry2@terry-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3745       3370        375          0        227       2235
-/+ buffers/cache:        906       2839
Swap:          500          0        500
terry2@terry-desktop:~$

---

### Post by kansasnoob on 2014-08-03
> **kirkcudbright said:**
> terry2@terry-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        76G   39G   33G  54% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           375M  1.2M  374M   1% /run
none            5.0M  8.0K  5.0M   1% /run/lock
none            1.9G  300K  1.9G   1% /run/shm
/dev/sdc1        30G   12G   18G  39% /media/linuxback
terry2@terry-desktop:~$ 


terry2@terry-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3745       3370        375          0        227       2235
-/+ buffers/cache:        906       2839
Swap:          500          0        500
terry2@terry-desktop:~$

I was curious about why such a small amount of swap but I see you have 4 GB of RAM so you probably seldom use swap anyway.

But df -h (I asked for df -H) shows that your Ubuntu root partition is over 50% (exactly 54%) used which makes things slightly more complicated. I typically like to keep total partition usage below 80% just to be on the safe side, but if you could reduce the amount of space used below 40% then you could shrink sda1 to about 1/2 of it's current size and create a new primary partition (sda2) using Gparted from the 14.04 live disc.

Like here's an 80 GB disc I used for testing an upgrade yesterday:

[ATTACH=CONFIG]255224[/ATTACH]

So I can right-click that existing partition and select Resize/Move:

[ATTACH=CONFIG]255225[/ATTACH]

Then shrink it by about 1/2:

[ATTACH=CONFIG]255226[/ATTACH]

Then right-click the new empty space and create a new partition:

[ATTACH=CONFIG]255227[/ATTACH]

Then simply click on the green checkmark to apply and you'll end up with a new partition (**[COLOR="#FF0000"]that operation may take quite a long time and must not be interrupted[/COLOR]**):

[ATTACH=CONFIG]255228[/ATTACH]

Then when you install you can select Something Else as the installation type and be sure to select the newly created partition (/dev/sdb3 in that example) for root "/". Then you'll have a dual boot. Then you can later delete the original 12.04 root partition after everything is setup, data transferred, etc - and then resize the 14.04 partition to use that free space.

**[COLOR="#FF0000"]I must however warn that there is always a risk of data loss involved with any repartitioning or installation so backup everything of importance! The data you don't backup is always the data you'll lose![/COLOR]**

---

### Post by kirkcudbright on 2014-08-03
hi
thanks for info
i will give it a go
i have already done a full backup

terry

---

