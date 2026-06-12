---
title: "messed up /boot partitions with duplicate UUID"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by gregsmith_to on 2009-12-27
I set this machine up about 20 months ago with two SATA drives. The first had 400MB /boot, 40G for /, a swap partition and the rest for /home. 

I set the second drive up with the same partition sizes, the idea being that I could do backups of the root files by doing image copies of /dev/sda1 to dev/sdb1 (for /boot) and /dev/sda2 to /dev/sdb2 (for /). 

But I just noticed that this has gone terribly wrong - the image copy clones the UUID and /etc/fstab names the partitions by UUID rather than by /dev/sda1.  So I know how to fix that - I can erase the duplicate-UUID or modify /etc/fstab.

But I need to straighten out the boot partitions somehow - I just today noticed that /dev/sdb1 is mounted as /boot (not dev/sda1, which has the same UUID but different content)  whereas in '/' the intended partition (/dev/sda2) is mounted. 

It seems to me that it's physically booting /dev/sda1 but eventually /dev/sdb1 is mounted as /boot, there could be all kinds of problems. since upgrades will probably put things in /dev/sdb1. Also, the choice of partitions might be different from boot to boot. This probably explains why the machine has been difficult to boot for some months (but I only do it every 2-3 months, usually after a kernel upgrade).



From the information below (and given that it's currently fairly happy) I believe that /dev/sda1 contains the 'good' boot info,which is being used to boot, and /dev/sda2 the 'good' root, so having /dev/sdb1 come up as /boot has only the effect of confusing upgrades (since kernel upgrades could go there instead of /dev/sda1). Is this correct? I can therefore fix
it by wiping out /dev/sdb1 (and /dev/sdb2 for good measure).

Here are the most recent files on /dev/sdb1 (current /boot) ls -lt


```

-rw-r--r-- 1 root root 7733613 2009-04-18 18:43 initrd.img-2.6.24-23-generic
drwxr-xr-x 2 root root    1024 2009-04-18 18:42 grub
-rw-r--r-- 1 root root 7733589 2009-04-18 18:42 initrd.img-2.6.24-23-generic.bak
-rw-r--r-- 1 root root  420395 2009-04-01 20:34 abi-2.6.24-23-generic
-rw-r--r-- 1 root root   74166 2009-04-01 20:34 config-2.6.24-23-generic
-rw-r--r-- 1 root root 1153489 2009-04-01 20:34 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1907704 2009-04-01 20:34 vmlinuz-2.6.24-23-generic
-rw-r--r-- 1 root root 7733674 2008-12-09 08:49 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7733526 2008-11-15 12:14 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7734432 2008-10-31 21:21 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root  420395 2008-10-21 21:49 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   74177 2008-10-21 21:49 config-2.6.24-21-generic
-rw-r--r-- 1 root root 1153201 2008-10-21 21:49 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1905688 2008-10-21 21:49 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 7734381 2008-09-18 09:04 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7734596 2008-08-24 11:30 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root  420224 2008-08-20 18:15 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   74164 2008-08-20 18:15 config-2.6.24-19-generic
-rw-r--r-- 1 root root 1152364 2008-08-20 18:15 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1903096 2008-08-20 18:15 vmlinuz-2.6.24-19-generic

```

... and on /dev/sda1

```

-rw-r--r-- 1 root root 7738439 2009-10-30 22:56 initrd.img-2.6.24-25-generic
drwxr-xr-x 2 root root    1024 2009-10-30 22:55 grub
-rw-r--r-- 1 root root 7738196 2009-10-30 22:55 initrd.img-2.6.24-25-generic.bak
-rw-r--r-- 1 root root 7738381 2009-10-30 22:55 initrd.img-2.6.24-24-generic
-rw-r--r-- 1 root root  420395 2009-10-20 05:29 abi-2.6.24-25-generic
-rw-r--r-- 1 root root   74228 2009-10-20 05:29 config-2.6.24-25-generic
-rw-r--r-- 1 root root 1154307 2009-10-20 05:29 System.map-2.6.24-25-generic
-rw-r--r-- 1 root root 1907736 2009-10-20 05:29 vmlinuz-2.6.24-25-generic
-rw-r--r-- 1 root root 7738683 2009-10-05 23:00 initrd.img-2.6.24-24-generic.bak
-rw-r--r-- 1 root root  420395 2009-09-18 14:56 abi-2.6.24-24-generic
-rw-r--r-- 1 root root   74166 2009-09-18 14:56 config-2.6.24-24-generic
-rw-r--r-- 1 root root 1154020 2009-09-18 14:56 System.map-2.6.24-24-generic
-rw-r--r-- 1 root root 1907672 2009-09-18 14:56 vmlinuz-2.6.24-24-generic
-rw-r--r-- 1 root root 7734273 2009-02-21 08:31 initrd.img-2.6.24-23-generic
-rw-r--r-- 1 root root 7733766 2009-01-21 21:08 initrd.img-2.6.24-23-generic.bak
-rw-r--r-- 1 root root 7733573 2008-11-29 12:52 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7733535 2008-11-29 12:52 initrd.img-2.6.24-22-generic.bak
-rw-r--r-- 1 root root  420395 2008-11-27 15:56 abi-2.6.24-23-generic
-rw-r--r-- 1 root root   74166 2008-11-27 15:56 config-2.6.24-23-generic
-rw-r--r-- 1 root root 1153225 2008-11-27 15:56 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1907096 2008-11-27 15:56 vmlinuz-2.6.24-23-generic
-rw-r--r-- 1 root root  420395 2008-11-24 17:19 abi-2.6.24-22-generic
-rw-r--r-- 1 root root   74177 2008-11-24 17:19 config-2.6.24-22-generic
-rw-r--r-- 1 root root 1153201 2008-11-24 17:19 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 1905656 2008-11-24 17:19 vmlinuz-2.6.24-22-generic
-rw-r--r-- 1 root root 7733526 2008-11-15 12:14 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7734432 2008-10-31 21:21 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root  420395 2008-10-21 21:49 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   74177 2008-10-21 21:49 config-2.6.24-21-generic
-rw-r--r-- 1 root root 1153201 2008-10-21 21:49 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1905688 2008-10-21 21:49 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 7734381 2008-09-18 09:04 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7734596 2008-08-24 11:30 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root  420224 2008-08-20 18:15 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   74164 2008-08-20 18:15 config-2.6.24-19-generic
-rw-r--r-- 1 root root 1152364 2008-08-20 18:15 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1903096 2008-08-20 18:15 vmlinuz-2.6.24-19-generic


```

/proc/version contains

```

Linux version 2.6.24-25-generic (buildd@crested) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Oct 20 06:49:12 UTC 2009

```

The contents of 'grub' dir on /dev/sdb1

```

-rw-r--r-- 1 root root    197 2008-04-05 09:17 default
-rw-r--r-- 1 root root     30 2008-04-05 09:17 device.map
-rw-r--r-- 1 root root   8660 2008-04-05 09:17 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-04-05 09:17 fat_stage1_5
-rw-r--r-- 1 root root     15 2008-04-05 09:17 installed-version
-rw-r--r-- 1 root root   9152 2008-04-05 09:17 jfs_stage1_5
-rw-r--r-- 1 root root   6718 2009-04-18 18:42 menu.lst
-rw-r--r-- 1 root root   6718 2009-04-18 18:42 menu.lst~
-rw-r--r-- 1 root root   7860 2008-04-05 09:17 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-04-05 09:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-04-05 09:17 stage1
-rw-r--r-- 1 root root 110292 2008-04-05 09:17 stage2
-rw-r--r-- 1 root root   9980 2008-04-05 09:17 xfs_stage1_5

```

The contents of 'grub' dir on /dev/sda1, almost the same

```

-rw-r--r-- 1 root root    197 2008-04-05 09:17 default
-rw-r--r-- 1 root root     30 2008-04-05 09:17 device.map
-rw-r--r-- 1 root root   8660 2008-04-05 09:17 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-04-05 09:17 fat_stage1_5
-rw-r--r-- 1 root root     15 2008-04-05 09:17 installed-version
-rw-r--r-- 1 root root   9152 2008-04-05 09:17 jfs_stage1_5
-rw-r--r-- 1 root root   8038 2009-10-30 22:55 menu.lst
-rw-r--r-- 1 root root   7962 2009-10-30 22:55 menu.lst~
-rw-r--r-- 1 root root   7860 2008-04-05 09:17 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-04-05 09:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-04-05 09:17 stage1
-rw-r--r-- 1 root root 110292 2008-04-05 09:17 stage2
-rw-r--r-- 1 root root   9980 2008-04-05 09:17 xfs_stage1_5

```

grub/menu.lst on /dev/sdb1 starts with 
```


title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=bf09a603-eb30-4062-a270-7d159b0c527f ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=bf09a603-eb30-4062-a270-7d159b0c527f ro single
initrd		/initrd.img-2.6.24-23-generic


```


... and on /dev/sda1 ...

```


title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-25-generic root=UUID=bf09a603-eb30-4062-a270-7d159b0c527f ro quiet splash
initrd		/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-25-generic root=UUID=bf09a603-eb30-4062-a270-7d159b0c527f ro single
initrd		/initrd.img-2.6.24-25-generic



```

---

### Post by oldfred on 2009-12-28
You just found out why not to clone disks that you keep mounted. You would do better to run a backup like rsync to copy all the files without copying internals. Clone is fine where you want an image that you may want to recover from but should be offline once created to avoid confusion.

To see how you are booting:

Boot Info Script 0.42 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by griffinjones on 2009-12-28
Release the permissions to 444 blah (write down the locations!) blah then manually configure grub from the loader. Reassign the mount points as well as locations. I know.

---

### Post by gregsmith_to on 2010-01-17
Sorry to let this go stale ... I unmounted sdb1, remounted /sda1 as /boot, then proceeded to erase the beginnings of sdb1 and sdb2. Then it worked OK (this was prior to swapping the SDB out for a larger one anyhow). Seems to be fine, I still need to get my nvidia driver working again, but that's another story.

The image backup is a lot faster than a normal copy when you have a lot of small files (and reasonably full partition)

It looks like I could do this as follows:
  (1) read UUID from sdb2
  (2) image copy sda2 to sdb2 (which is faster than a normal copy if it's got a lot of small files)
  (3) restore sdb2 UUID to what it was before with tune2fs -U
(or use a new one each time via uuidgen)

---

