---
title: "KARMIC - Update Manager - Not enough free disk space?"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by bige40wings on 2010-01-10
I'm getting the "Not enough free disk space" error when I run Update Manager. I've read through some threads and found that those experiencing this didn't make their root partition large enough. I read about the 2.5GB installation "bug". None of this explains what has happened on my system. Let me explain.

I am dual booting Windows Vista Business and Ubuntu 9.10 Karmic on a Laptop PC with 60GB Hard drive space. My partitions are as follows:

```

sudo fdisk -l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  83  Linux
/dev/sda2   *           7        3193    25599577+   7  HPFS/NTFS
/dev/sda3            3194        6597    27342630    5  Extended
/dev/sda4            6598        7113     4142080    7  HPFS/NTFS
/dev/sda5            3194        6232    24410736   83  Linux
/dev/sda6            6233        6597     2931831   82  Linux swap / Solaris

``` Basically:
```

/boot (ext2)          47.03MB  31.99MB Used  15.05MB Unused
Windows Vista (ntfs)  24.41GB               
extended partition with:
   / (ext4)           23.28GB   4.04GB Used  19.24GB Unused
     linux-swap        2.80GB
Pagefile (ntfs)        3.95GB

```Disk Usage Analyzer results:
```

Folder     Usage      Size    Contents
 /        100.0%     3.5GB    19 items
 > usr     82.5%     2.9GB     8 items
 > var      6.2%   221.1MB    13 items 
 > lib      5.5%   196.9MB   102 items
 > home     4.3%   154.4MB     1 item
 > boot     0.8%    29.8MB    15 items
 > etc      0.4%    13.4MB   236 items
   sbin     0.2%     7.9MB   137 items
   bin      0.1%     5.3MB   103 items
 > dev      0.0%     1.4MB    15 items
 > srv      0.0%   200.0KB     1 item
 > tmp      0.0%    44.0KB     8 items
 > media    0.0%     8.0KB     1 item
   mnt      0.0%     4.0KB     0 items
   opt      0.0%     4.0KB     0 items
   selinux  0.0%     4.0KB     0 items

```So why is the filesystem only giving root 3.5GB of space? I have over 19GB of free space on the linux ext4 partition, but root is full. Why?

---

### Post by k64 on 2010-01-10
Try running an upgrade or updates from the terminal and see if that helps.

FAQ: How do you update form the terminal? This is how:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Any of these commands will work. If you still get the error, your disk probably is full, and you'll have to clear it.

---

### Post by drs305 on 2010-01-10
> **bige40wings said:**
> So why is the filesystem only giving root 3.5GB of space? I have over 19GB of free space on the linux ext4 partition, but root is full. Why?

Check out this guide for resolving disk space issues. The common reasons are undeleted trash, large log files, small boot partitions and backups mistakenly saved to the system partition instead of a backup partition.
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by bige40wings on 2010-01-10
Thanks, don't know why I didn't think of that. It's working so far. I'll post again with the results.

---

### Post by bige40wings on 2010-01-10
Updating from the terminal worked successfully, but at the end a pop-up notified me of the low disk space. I've learned that Ubuntu usually allocates 5% of the root partition for the system. You can change that percentage with:

```

**[COLOR=DarkRed][B]sudo tune2fs -m [B][COLOR=Red]X[/COLOR]** /dev/sd[COLOR=Red]XX[/COLOR][/B][/COLOR][/B]
```
where X is the percentage and sdXX is the root partition. Instead of decreasing the percentage, I increased it to 30% because I don't store anything on this laptop.

```

:~$  df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             24027628   3673584  13030824  22% /
udev                    509160       280    508880   1% /dev
none                    509160      1168    507992   1% /dev/shm
none                    509160        84    509076   1% /var/run
none                    509160         0    509160   0% /var/lock
none                    509160         0    509160   0% /lib/init/rw
/dev/sda1                46633     17300     26925  40% /boot

```

I won't really know if the problem is fixed until there are new updates to download. I'll have to come back in a few days and post the results.

---

### Post by bige40wings on 2010-01-10
This was apparently all about the boot partition. Update Manager was downloading a new kernel and headers. I had to clear out the old ones and it appears to be solved. I still want to wait a few days to be certain.

---

