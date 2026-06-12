---
title: "Bytes Per Inode"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by metalf8801 on 2011-05-14
How many bytes per inode do I get when using Standard Parameters? Do I get more or less than if I use News where I get One Inode Per 4KB Block? Does anyone know where I can find more information about this? None of the documentation I've found explains what "Standard Parameters" means. I've been able to figure out that I need one Inode for every file I have on my system. 


I'm installing Ubuntu Server on a WD20EARS with 4096 sectors (in case that matters) and I'm just trying to make sure I fully understand all of the steps I'm going through. I attached a screen shot of the screen I'm trying stuck on. 

 
Thank you 
Dan

---

### Post by dabl on 2011-05-14
I would guess that "standard" reverts to the legacy 512 bytes per inode, but I don't know it for a fact.  I would definitely go with their "news" option, and try it that way, and you should get great performance if you have a typical mix of large and small files ...

HOWEVER, alignment of the partition start sector appears to be an issue:  [http://www.maximumpc.com/article/news/linux_ready_4096_byte_sector_hard_drives](http://www.maximumpc.com/article/news/linux_ready_4096_byte_sector_hard_drives)

In other words, you need to set the start sector for the first partition (and any succeeding partitions) to a multiple of 4k.  If you don't know how to use fdisk to do that, here is the guide I used to align an SSD to 512k sectors:  [http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226)

The principle is the same for your drive as for the SSD with its 512k erase blocks.  It's a little dense, but with your calculator handy it's not above the average geek's ability.  :)

---

### Post by metalf8801 on 2011-05-14
> **dabl said:**
> I would guess that "standard" reverts to the legacy 512 bytes per inode, but I don't know it for a fact.  I would definitely go with their "news" option, and try it that way, and you should get great performance if you have a typical mix of large and small files ...

HOWEVER, alignment of the partition start sector appears to be an issue:  [http://www.maximumpc.com/article/news/linux_ready_4096_byte_sector_hard_drives](http://www.maximumpc.com/article/news/linux_ready_4096_byte_sector_hard_drives)

In other words, you need to set the start sector for the first partition (and any succeeding partitions) to a multiple of 4k.  If you don't know how to use fdisk to do that, here is the guide I used to align an SSD to 512k sectors:  [http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226)

The principle is the same for your drive as for the SSD with its 512k erase blocks.  It's a little dense, but with your calculator handy it's not above the average geek's ability.  :)

Thank you and I think I've already aligned the partition correctly, but I'll take at look at that how to anyway.

---

### Post by srs5694 on 2011-05-14
I'm pretty sure that this parameter doesn't affect alignment, nor is it really about the number of bytes consumed by inodes; rather, it's about how many inodes are created on the filesystem. I think it's referring to the -i option to mke2fs, which is described in its man page:

[quote=mke2fs man page]
-i bytes-per-inode

Specify the bytes/inode ratio. mke2fs creates an inode for every bytes-per-inode bytes of space on the disk. The larger the bytes-per-inode ratio, the fewer inodes will be created. This value generally shouldn't be smaller than the blocksize of the filesystem, since in that case more inodes would  be made than can ever be used. Be warned that it is not possible to expand the number of inodes on a filesystem after it is created, so be careful deciding the correct value for this parameter.
[/quote]

To further understand this, know that an inode is a filesystem data structure that stores information on a file. Every file needs one inode. The ext2/3/4fs family pre-allocates inodes, which means that every ext2/3/4 filesystem has a fixed number of files it can support, defined at the moment the filesystem is created. (Some filesystems, such as ReiserFS, allocate inodes dynamically, so you don't need to make such decisions at the start.)

The "news" setting is named for Usenet news servers, which tend to accumulate huge numbers of extremely small files; this setting allocates lots of inodes to support the large number of files. The "standard" setting is good for general-purpose systems; it allocates fewer inodes, but still plenty for most uses. The "largefile" and "largefile4" settings are good for systems that store very large files (such as a partition for holding MythTV recordings, which are usually gigabytes in size); these allocate fewer inodes, but enough to store all the multi-gigabyte files you could cram onto the disk.

If you select an improper value, the consequences will vary with what you choose. If you select the "news" setting and then store big multimedia files, you'll have tied up too much of your disk space in inodes, so your disk space will be wasted. If you select the "largefile4" setting and then store lots of little ~2 KiB files, you'll run out of inodes and be unable to store more files on the disk despite having lots of free space available.

FWIW, you can view the number of inodes used and available with "df -i", as in:

```
$ **df -i**
Filesystem        Inodes   IUsed       IFree IUse% Mounted on
/dev/sda8        1222992  292410      930582   24% /
/dev/sda5          97344     223       97121    1% /boot
/dev/sda4     4294967295    3015  4294964280    1% /other/shared
/dev/sda1              0       0           0    -  /boot/efi
/dev/sda10       2297456    2772     2294684    1% /home

```

This was taken on a fairly stock Ubuntu 11.04 installation (upgraded from 10.10). I've cut several filesystems from this example for clarity. The /boot/efi partition is FAT, which doesn't use inodes per se, so the values are reported as 0. (You'd see something similar for ReiserFS.) The /boot partition is a small ext2 filesystem, root (/) is ext4fs and holds the bulk of the installation (6.1 GiB used out of 19 GiB). /other/shared is an HFS+ partition that's barely used right now, and /home is an ext4 filesystem that's also mostly empty at the moment. I didn't tweak the inode settings for any of these filesystems; they're all set at default values.

Although this has nothing to do with the 4 KiB alignment required for a WD20EARS drive, you should definitely pay attention to that issue. I wrote [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) about it a while ago. The short advice is to use "fdisk -lu", "parted /dev/sd{whatever} unit s print", "gdisk -l /dev/sd{whatever}", or some other command or tool to view the *start* sector of every partition. Ensure that the start sector number is divisible by 8. If it's not, delete the partition and start over again, using whatever options your favored partitioning tool provides to ensure the start sector number is divisible by 8. (The end sector number is irrelevant. So is the start value of your extended partition, if you've got one.) The good news is that all the major Linux partitioning tools have switched to creating partitions that begin on 1 MiB (2048-sector) boundaries by default, and since 2048 is divisible by 8, you'll probably do fine if you use a recent tool and its defaults. The bad news is that Linux partitioning tools were slow to make this change (Microsoft began doing this with Vista), so a lot of older tools are still out there that will misalign your partitions if you don't watch over them very carefully.

---

### Post by dabl on 2011-05-15
@srs5694, this is _most_ instructive, thank you for posting it.

Among other things I gleaned, I see now that one can use the df -i output to compare with df -h, and see how efficient, or inefficient, one's working filesystems are, in terms of inode utilization.  On my main desktop system, which I built last November, here is my comparison (with tmpfs filesystems deleted):

```
# df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sdc1            3375104  209338 3165766    7% /
/dev/sdd1            3670016     252 3669764    1% /mnt/REVODATA
/dev/sde1             131072     249  130823    1% /boot
/dev/sde2             944704      12  944692    1% /mnt/WHATEVER
/dev/sdb                   0       0       0    -  /mnt/DATA

# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              51G   11G   41G  21% /
/dev/sdd1              56G   47G  8.8G  85% /mnt/REVODATA
/dev/sde1             495M   54M  416M  12% /boot
/dev/sde2              15G  165M   15G   2% /mnt/WHATEVER
/dev/sdb              1.9T  472G  1.4T  26% /mnt/DATA
```

/dev/sdb is a btrfs filesystem so it does not report inode usage.  It looks like my "/" filesystem was a little wasteful in terms of creating more inodes than will ever be needed, but it's not a disaster.  The /dev/sdd1 filesystem is pretty much a disaster in this respect -- it could have done with a far smaller allocation of inodes, i.e. far larger bytes-per-inode value when the filesystem was created.  It happens that /dev/sdd1 contains mainly some large (10GiB ~ 20GiB) VMs, so it makes sense that it would not be efficient with a default inode value.

Great info for future use -- thanks again!  :)

---

