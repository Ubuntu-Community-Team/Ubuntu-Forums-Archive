---
title: "constant check disc that never fixes itself"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2013-12-23
Hi All,

I've been struggeling with 13.10, recentl;y trying to run Gnome 3.

I have a dual boot system with Xubuntu 13.04 and Gnome 13.10 on a 128 GB SSD. The 13,04 xubuntu runs well. But, whenever I boot to the Gnome 3 partition, I have to wait for the disc check, then wait while the entire system restarts starting from the POST beep. 

Other than this problem, 13.10 Gnome runs well too.

See the attached file for a gparted screenshot of the drive.

I booted from the liveCD (usb version) and did the following tests:

[HTML]GParted 0.16.1 --enable-libparted-dmraid
 Libparted 2.3
    Check and repair file system (ext4) on /dev/sda6  00:00:02    ( SUCCESS )             calibrate /dev/sda6  00:00:00    ( SUCCESS )             path: /dev/sda6
start: 21168128
end: 72368127
size: 51200000 (24.41 GiB)          check file system on /dev/sda6 for errors and (if possible) fix them  00:00:02    ( SUCCESS )             e2fsck -f -y -v /dev/sda6             Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      421084 inodes used (26.23%, out of 1605632)
        1119 non-contiguous files (0.3%)
         306 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 374958/408/5
     3873674 blocks used (60.53%, out of 6400000)
           0 bad blocks
           1 large file

      306874 regular files
       59620 directories
          57 character device files
          25 block device files
           0 fifos
          14 links
       54498 symbolic links (45622 fast symbolic links)
           1 socket
------------
      421089 files
       e2fsck 1.42.8 (20-Jun-2013)
             grow file system to fill the partition  00:00:00    ( SUCCESS )             resize2fs /dev/sda6              
      resize2fs 1.42.8 (20-Jun-2013)
The filesystem is already 6400000 blocks long.  Nothing to do!
[/HTML]



[HTML]GParted 0.16.1 --enable-libparted-dmraid
 Libparted 2.3
    Check and repair file system (ext2) on /dev/sda7  00:00:10    ( SUCCESS )             calibrate /dev/sda7  00:00:00    ( SUCCESS )             path: /dev/sda7
start: 131420160
end: 233820159
size: 102400000 (48.83 GiB)          check file system on /dev/sda7 for errors and (if possible) fix them  00:00:10    ( SUCCESS )             e2fsck -f -y -v /dev/sda7             Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      225391 inodes used (7.08%, out of 3184304)
        1019 non-contiguous files (0.5%)
         272 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 9252/179/0
     2187975 blocks used (17.09%, out of 12800000)
           0 bad blocks
           1 large file

149222 regular files
       22959 directories
          57 character device files
          25 block device files
           0 fifos
           7 links
       53118 symbolic links (43002 fast symbolic links)
           1 socket
------------
      225389 files
       e2fsck 1.42.8 (20-Jun-2013)
             grow file system to fill the partition  00:00:00    ( SUCCESS )             resize2fs /dev/sda7              
      resize2fs 1.42.8 (20-Jun-2013)
The filesystem is already 12800000 blocks long.  Nothing to do!
[/HTML]


```
artie@artsplace-1310G:~$ sudo badblocks -v /dev/sda7 > bad-blocks
[sudo] password for artie: 
Checking blocks 0 to 51199999
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
artie@artsplace-1310G:~$
```


```
artie@artsplace-1310G:~$ sudo badblocks -v /dev/sda7 > bad-blocks
[sudo] password for artie: 
Checking blocks 0 to 51199999
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
artie@artsplace-1310G:~$ 
```


At one point, I ran gparted check and fix errors if possible. This caused my system to be unbootable and 'sudo update-grub' wouldn't run. I booted to the liveCD, created another small partition and installed gnome 13.10 in that partition. When it restarted, the system would boot again, I think the liveCD install updated the grub. 

Currently I can boot to 13.04 Xubuntu on sda6 and can boot to 13.10 Gnome on SDA7 (with the constant disc checks occuring).

Did I do something wrong, or is this another issue with 13.10 bugs? 

Any ideas?

TIA

Art

---

### Post by goodbye-windows(tm) on 2013-12-23
I left out the fsck results.........

They indicate SDA7 was not cleanly unmounted. Is this a possible bug associated with 13.10??

```
ubuntu-gnome@ubuntu-gnome:~$ sudo fsck /dev/sda7
fsck from util-linux 2.20.1
e2fsck 1.42.8 (20-Jun-2013)
/dev/sda7 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda7: 225390/3184304 files (0.6% non-contiguous), 2187884/12800000 blocks
```


```
ubuntu-gnome@ubuntu-gnome:~$ sudo fsck /dev/sda6
fsck from util-linux 2.20.1
e2fsck 1.42.8 (20-Jun-2013)
/dev/sda6: clean, 421084/1605632 files, 3873674/6400000 blocks
ubuntu-gnome@ubuntu-gnome:~$
```

Art

---

