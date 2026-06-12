---
title: "Unrecoverable error during installation on Lucid"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ktz84 on 2010-05-02
I've tried to do a fresh install of Lucid and each time I'm getting an unrecoverable error and it then takes me to a desktop version from which I can run an installer however that then crashes when trying set up the /home partition.

I've no idea where to start to resolve this.

The latest attempt at an install from boot rather than the desktop session has the following in the syslog.

> May  2 11:08:38 ubuntu acpid: 1 client rule loaded
May  2 11:08:39 ubuntu gdm-session-worker[2775]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  2 11:08:47 ubuntu pulseaudio[2730]: ratelimit.c: 3 events suppressed
May  2 11:08:49 ubuntu kernel: [  139.239278] ondemand governor failed, too long transition latency of HW, fallback to performance governor
May  2 11:08:51 ubuntu acpid: client connected from 2986[108:114]
May  2 11:08:51 ubuntu acpid: 1 client rule loaded
May  2 11:09:18 ubuntu ubiquity[3058]: Ubiquity 2.2.24
May  2 11:09:21 ubuntu ubiquity[3058]: log-output -t ubiquity laptop-detect
May  2 11:09:23 ubuntu ubiquity[3058]: log-output -t ubiquity laptop-detect
May  2 11:09:27 ubuntu ubiquity[3058]: switched to page languageDon't if that is any help to anyone. Help greatly appreciated.

---

### Post by ktz84 on 2010-05-02
Ok as I was having trouble creating the /home partition in the Desktop install I decided to try and create the partition in GParted.

Both ext4 and ext3 fail to format.

The ext4 fail gparted file looks like this:

> GParted 0.5.1
 Libparted 2.2
    **Format /dev/sda6 as ext4**  00:01:32    ( ERROR )             calibrate /dev/sda6  00:00:00    ( SUCCESS )             [I]path: /dev/sda6
start: 141615104
end: 395165695
size:  253550592 (120.90 GiB)[/I]          set partition type on /dev/sda6  00:00:01    ( SUCCESS )             *new partition type: ext4*          create new ext4 file system  00:01:31    ( ERROR )             ***mkfs.ext4 -j -O extent -L "" /dev/sda6***             [I]Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment  size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
7929856  inodes, 31693824 blocks
1584691 blocks (5.00%) reserved for the super  user
First data block=0
Maximum filesystem blocks=0
968 block  groups
32768 blocks per group, 32768 fragments per group
8192  inodes per group
Superblock backups stored on blocks: 
	32768,  98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	 4096000, 7962624, 11239424, 20480000, 23887872

Writing inode  tables: done                            
Creating journal (32768  blocks): done
Writing superblocks and filesystem accounting  information: done

This filesystem will be automatically checked  every 35 mounts or
180 days, whichever comes first.  Use tune2fs -c  or -i to override.
[/I]       [I]mke2fs 1.41.11 (14-Mar-2010)

Warning, had trouble writing out  superblocks.[/I]             ========================================


I can however format the space to fat32 and ntfs with gparted. So not sure if that helps at all.

---

### Post by ktz84 on 2010-05-02
I managed to get the /home directory to format by increasing the size of the partition 10gb at a time. Not sure why that helped but it worked.

---

### Post by dino99 on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by ktz84 on 2010-05-02
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

Thanks I'll bear that in mind for the next install. I used the built in partioner in the installer, I then used gparted and when that didn't work I then used the disk analzyer tool which allows you to format partitions but it failed like just all the rest. They all complained about not being able to move superblocks whatever they are.

Ah well up and running now even if I can't get my wireless network card working (2 different ones) but that's another question.

---

