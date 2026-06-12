---
title: "There is not enough disk to save the file.Please free some disc space and try."
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by milenko-markovic on 2015-08-04
I am on Ubuntu 14.04. I tried to save small cpp file.How should I solve this problem?
```
milenko@milenko-HP-Compaq-6830s:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00024e07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484214783   242106368   83  Linux
/dev/sda2       484216830   488396799     2089985    5  Extended
/dev/sda5       484216832   488396799     2089984   82  Linux swap / Solaris

milenko@milenko-HP-Compaq-6830s:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       228G  216G  290M 100% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            984M  4,0K  984M   1% /dev
tmpfs           200M  1,2M  199M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            999M   22M  977M   3% /run/shm
none            100M   48K  100M   1% /run/user
```

---

### Post by ian-weisser on 2015-08-04
I don't understand the question.
Your disk is full. You must either delete files or add more storage.

---

### Post by howefield on 2015-08-04
Try running

```
sudo apt-get clean
```
```
sudo apt-get autoremove
```

---

### Post by Topsiho on 2015-08-04
+1 to howefield.

Every time you update, files are saved on your disk which you don't need anymore after the updates, but in the long run fill up your hard disk.
The commands that howefield advises remove those files, and may be remarkably effective in getting your computer up and running again :)

The second one (autoremove) removes linux images and header files, except the last 2 versions, but unfortunately doesn't work in all Ubuntu's. I have a Lubuntu 14.04, on one of my computers, in which it doesn't work, and I have to wipe these images manually, which I do using Synaptic (Linux-image files and Linux-header files), taking care to keep the last two versions.

Topsiho

---

