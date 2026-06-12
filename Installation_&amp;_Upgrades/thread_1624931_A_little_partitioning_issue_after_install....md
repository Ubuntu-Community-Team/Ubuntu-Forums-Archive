---
title: "A little partitioning issue after install..."
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by santosh83 on 2010-11-18
Hi all,

I very recently installed Maverick Meerkat on my desktop, and during installation, chose to allow it to erase and use my entire harddisk, which is a 40 Gb Samsung PATA, mounted under /dev/sda by Linux. Just doing a 

```
sudo sfdisk -l /dev/sda
```for curiosity shows:

```
Disk /dev/sda: 4865 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   4660-   4660-  37431296   83  Linux
/dev/sda2       4660+   4865-    206-   1648641    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       4660+   4865-    206-   1648640   82  Linux swap / Solaris

```Is this normal/OK? I have manually partitioned before when i used to use RedHat and would always ensure that paritions start and end at cylinder boundaries (if not, deleting & redoing), though i never enquired why it had to be so. For some strange reason I always preferred an OK output from 

sfdisk -V my_disk

and it irks me that it now shows: 

```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 1 does not end at a cylinder boundary
```So to come to my point, is this something I need not worry about other than that its not aesthetically pleasing? Partitions /dev/sda3 and /dev/sda4 seem to be spurious ones, and I would've thought that when using the whole disk the install program would simply opt for two primary partition (/ and swap) instead of a primary & extended.

And for curiosity's sake, why do partitioning programs sometimes create partitions not starting or ending at cylinder boundaries (adjusting their sizes if need be), provided enough space was available, as was the case here?

Thank you all.

---

### Post by viralmeme on 2010-11-18
> **santosh83 said:**
> ```

/dev/sda1   *      0+   4660-   4660-  37431296   83  Linux
/dev/sda2       4660+   4865-    206-   1648641    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       4660+   4865-    206-   1648640   82  Linux swap / Solaris

```

No idea why it's doing that. You only create an Extended partition if you need more than four partitions. You could boot from the live cd run Gparted, delete sda2-sda5, then recreate the swap partition. You will need to change the line in fstab to point to the new swap partition, which presumably will be sda2.

/dev/hda2       none            swap    sw              0       0

---

### Post by ottosykora on 2010-11-18
well the alingment of the partitions is something not very much concerning you if your disk ist PATA, this type will quite sure use old style of sectors, partiton starting at sector 63 and so on.

When you create new partitons, you can select the align to cylinder function, called so or similar, then it will take care of the alingment.

Very new disks on the market do use in fact different sector size and there the whole thing will become important.

---

### Post by santosh83 on 2010-11-18
> **viralmeme said:**
> No idea why it's doing that. You only create an Extended partition if you need more than four partitions. You could boot from the live cd run Gparted, delete sda2-sda5, then recreate the swap partition. You will need to change the line in fstab to point to the new swap partition, which presumably will be sda2.

/dev/hda2       none            swap    sw              0       0

Yes that's an idea. In my /etc/fstab while /dev/sda1 (which is the / partition) is named as such, /dev/sda5 (for swap) is named by it's UUID, which i'm guessing will change when I delete sda2, sda3, sda4 and sda5, and recreate sda2 as a primary for swap.

In any case if this cylinder boundary issue is not going to be a problem down the road, then it's probably better to just leave it as it is.

Thanks for the reply!

---

### Post by santosh83 on 2010-11-18
> **ottosykora said:**
> well the alingment of the partitions is something not very much concerning you if your disk ist PATA, this type will quite sure use old style of sectors, partiton starting at sector 63 and so on.

When you create new partitons, you can select the align to cylinder function, called so or similar, then it will take care of the alingment.

Very new disks on the market do use in fact different sector size and there the whole thing will become important.

Yes when I partition manually, I always round the sizes so that this type of situation doesn't arise but I opted for the automatic partitioning during installation since I was letting it use the whole disk. Even a year or two ago I'd partition such that /, /boot, /usr, /usr/local, /var, /tmp, /opt and /home resided on individual partitions, but found that often some partitions became too full with wasted space on others, so I decided to go with a single big one for everything under /, just allowing the install program do it's thing.

Anyway I guess I can safely ignore this issue. Thanks for the reply!

---

### Post by Mike_tn on 2010-12-04
I have the same warning when I run
sudo sfdisk -d /dev/sda > backup.txt

[B]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.[/B]

and I use a new laptop by Dell with Windows 7. Dell made the partition it is whining about. Which is about  50GB for the Windows 7 OS and then just added partitions to the remaining open space. I put an NTFS logical data partition right next to W7.  like this>

**|**W7-Primary**|**Data-Logical**|**Ubuntu**|**Swap[B]|

[/B]Everything runs perfectly smooth. But I was concerned about it being a future problem. Could it be?

---

### Post by oldfred on 2010-12-04
Since they started to use Large Block addressing for drives (about 10 years ago they started) in place of CHS cylinder, heads, sectors it has not mattered. Because the partitioning tools used cylinder boundary equivalents, you did not see it, i.e. starting at 63. Windows converted to sector 2048 as the start of the first partition and now gparted/Ubuntu have also for compatibility with newer drives.

Or it does not matter.

---

### Post by Mike_tn on 2010-12-04
Most appreciated [oldfred]("http://ubuntuforums.org/member.php?u=852711")

---

