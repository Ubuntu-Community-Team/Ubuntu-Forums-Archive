---
title: "Make Ubuntu Use all of my HDD."
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by MikeVaughanG on 2011-09-18
So, Here's the deal. 
I just installed gparted. 
I would like to know if there is a way I could keep all of my files and information, and somehow give Ubuntu access to all of the space on my HDD. 

Currently I have a Windows partition, but this is my first time partitioning at all, and I don't wanna mess anything up. And I dont want the Windows partition at all. 

So, How do I increase the size of my Ubuntu partition, and delete the Windows one using gparted or any other tool?

Any help is greatly appreciated.

---

### Post by Hakunka-Matata on 2011-09-18
Hi, Welcome,

Please post the output of ```
sudo sfdisk -luS && sudo fdisk -lu
``` so we can see how your drive is partitioned now, then see how it could be changed.

---

### Post by MikeVaughanG on 2011-09-18
> **Hakunka-Matata said:**
> Hi, Welcome,

Please post the output of ```
sudo sfdisk -luS && sudo fdisk -lu
``` so we can see how your drive is partitioned now, then see how it could be changed.

Gladly :)


```
 Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2     313446398 1250242559  936796162   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     625121343 1250242559  625121217  83  Linux
/dev/sda6     313446400 617170943  303724544  83  Linux
/dev/sda7     617172992 625121279    7948288  82  Linux swap / Solaris

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e3f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       313446398  1250242559   468398081    f  W95 Ext'd (LBA)
/dev/sda5       625121343  1250242559   312560608+  83  Linux
/dev/sda6       313446400   617170943   151862272   83  Linux
/dev/sda7       617172992   625121279     3974144   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Hakunka-Matata on 2011-09-18
sda5 & sda6 are both type 83 linux partitions:

[LIST]
[*]which one is your OS?, this will tell us:
[LIST]
[*]```
df -h
```
[/LIST]
[*]what's on the other linux partition (sda5 or sda6)?  do you  have a /home partition?
[/LIST]

---

### Post by MikeVaughanG on 2011-09-18
> **Hakunka-Matata said:**
> sda5 & sda6 are both type 83 linux partitions:

[LIST]
[*]which one is your OS?, this will tell us:
[LIST]
[*]```
df -h
```
[/LIST]
[*]what's on the other linux partition (sda5 or sda6)?  do you  have a /home partition?
[/LIST]

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             143G   51G   86G  38% /
none                  1.9G  680K  1.9G   1% /dev
none                  1.9G  5.2M  1.9G   1% /dev/shm
none                  1.9G  156K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda5             294G  191M  279G   1% /media/9c8938e3-a3e2-4f8f-aafe-e1e3a3919117

```

I believe /sda6

---

### Post by Hakunka-Matata on 2011-09-18
/dev/sda5             294G  191M  279G   1% /media/9c8938e3-a3e2-4f8f-aafe-e1e3a3919117

sda6 is the operating system partition, do you have data stored in it also?  
sda5 appears to have nothing in it, but I don't know that for sure, can you have a look in it to see if it's important, or ok to delete?
Is this what you wanted to do?, check things out before charging ahead?

---

### Post by MikeVaughanG on 2011-09-18
> **Hakunka-Matata said:**
> /dev/sda5             294G  191M  279G   1% /media/9c8938e3-a3e2-4f8f-aafe-e1e3a3919117

sda6 is the operating system partition, do you have data stored in it also?  
sda5 appears to have nothing in it, but I don't know that for sure, can you have a look in it to see if it's important, or ok to delete?
Is this what you wanted to do?, check things out before charging ahead?

The operating system filesytem is the only thing I wanna save.

---

### Post by MikeVaughanG on 2011-09-18
And sda5 is okay to erase.

---

### Post by Hakunka-Matata on 2011-09-18
so what's mounted in /media?, is that a CD you have inserted in your machine now?

---

### Post by Hakunka-Matata on 2011-09-18
> **MikeVaughanG said:**
> And sda5 is okay to erase.
I won't tell you it's ok to delete, I don't know what's in it.
have a look at it, 
```
cd /mnt
ls

```

---

### Post by MikeVaughanG on 2011-09-18
the only thing in /media is a folder named 'external'

So, here's what I did. I opened a file browser with 
```
 sudo nautilus 
```

And deleted 'external'

Now when I do 
```
 df -h 
```

I get this 
```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             143G   51G   85G  38% /
none                  1.9G  680K  1.9G   1% /dev
none                  1.9G  5.2M  1.9G   1% /dev/shm
none                  1.9G  156K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock

```

---

### Post by Hakunka-Matata on 2011-09-18
so you either unmounted it, or deleted sda5 EDIT: i just saw you said you deleted external

what's next

---

### Post by MikeVaughanG on 2011-09-18
> **Hakunka-Matata said:**
> so you either unmounted it, or deleted sda5 EDIT: i just saw you said you deleted external

what's next


Im not sure, I just want sda6 to use all of the memory on the hdd. But I dont know how to do that.

---

### Post by MikeVaughanG on 2011-09-18
I bet I need to boot from a live disk, and so I can unmount the os filesytem, but that's just my best guess.Im new.

---

### Post by YesWeCan on 2011-09-18
This may help: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Using live CD, in GParted you may want to resize sda2, the extended partition, and move the left boundary right to the left so as to include the first part of your disk. Then resize sda6 and move its left boundary to the start of sda2.

---

### Post by MikeVaughanG on 2011-09-18
I think I'm gonna try to use a Gparted-live USB.

---

