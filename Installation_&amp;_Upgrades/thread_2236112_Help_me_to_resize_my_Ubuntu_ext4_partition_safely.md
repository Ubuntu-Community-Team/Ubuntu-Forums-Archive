---
title: "Help me to resize my Ubuntu ext4 partition safely"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by spiritualbird on 2014-07-24
When I started using Ubuntu 12.04 two years before, it was just for experiencing a new OS. But eventually I have fallen in love with this secure, fast, intuitive OS. Now I am using 13.10. But my Ubuntu drive was the one created first time, which is only 15 GB. Now I cannot live without Ubuntu. I hate the sluggish, buggy, infected windows 7 greatly (I use it in dual boot). It only gives me pain when I try to use Windows 7. But now as my free Ubuntu drive space goes below 2 GB (now 1.4 GB), it is also giving me pain - in hangs frequently, sometimes I cannot access to net real time etc. I think these are outcome of low free space (please correct me if I am wrong). 

I have read some articles regarding extending the drive, but they all seems too complicated. I will be able to boot Ubuntu from a Live CD (inshaAllah), and will be able to use Gparted from that (inshaAllah). Please help me, how can I safely unallocate some space from my **sda3** and then add that to **sda6 (ubuntu)**. 

Here is my fsdik -lu and parted -l information respectively:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x72a980e5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   137482221    68740087    7  HPFS/NTFS/exFAT
/dev/sda2       137484331   393822207   128168938+   f  W95 Ext'd (LBA)
/dev/sda3       393822208   685275135   145726464    7  HPFS/NTFS/exFAT
/dev/sda4       685275136   976773119   145748992    7  HPFS/NTFS/exFAT
/dev/sda5       137484333   362360129   112437898+   7  HPFS/NTFS/exFAT
/dev/sda6       362360832   385648639    11643904   83  Linux
/dev/sda7       385650688   393822207     4085760   82  Linux swap / Solaris



```

```
Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  70.4GB  70.4GB  primary   ntfs            boot
 2      70.4GB  202GB   131GB   extended                  lba
 5      70.4GB  186GB   115GB   logical   ntfs
 6      186GB   197GB   11.9GB  logical   ext4
 7      197GB   202GB   4184MB  logical   linux-swap(v1)
 3      202GB   351GB   149GB   primary   ntfs
 4      351GB   500GB   149GB   primary   ntfs



```

Please give me a safe process by which I will be able to enlarge my Ubuntu drive by 45 GB. Now it is 15 GB, I want to make it 60 GB. 

I am a novice, please use simple instruction while you prepare your process.

P.S. I have read from a post that, it is critical to swap space from a drive, which is not adjacent to Ubuntu drive. In my case, I have another drive (linux swap drive) in between. So, suggest me, what should I do, at this complicated scenario.

---

### Post by TheFu on 2014-07-24
The only safe, non-complex, way to do what you want is to buy a larger HDD and clone the 1st onto the 2nd. 

Every other method includes risks of data loss.  There are a few different ways to accomplish this, but they all start by having a good, know-you-can-restore backup without god's help.

Reduce the size of /dev/sda5 using Windows, then boot off a liveCD and use gparted to give that storage to sda6.  Does that make sense? Only the storage "inside" the extended partition can be used.

---

### Post by vanadium on 2014-07-25
The by far safest approach, since you are dual booting anyway, is to keep all your user data on the large ntfs partitions. Then you can access all of your data from within both operating systems.

Symbolic links allow you to conveniently access data no matter where it is. if you replace your "Documents" folder by a symbolic link to your data folder of your Windows system, then you will be using that data the same way as if you had a separate Documents folder on your linux partition. You will however want to mount your ntfs partition automatically in that scenario, thought. Otherwise, after startup, you first would need to click the partition in the file manager each time before you could access your documents.

The only caveat using that approach is that you have to make sure to shut down Windows completely (= no hibernation but full shut down) before booting to linux. Linux will only mount an ntfs partition provided it has been correctly closed.

Repartitioning, of course, remains an option. With your current layout, though, you would need to move the sda6 partition to the front. This is a process that will run for a long time without full guarantee that it will succeed successfully. If instead you could enlarge a partition by extending it to the right, it would  be a matter of seconds.

---

