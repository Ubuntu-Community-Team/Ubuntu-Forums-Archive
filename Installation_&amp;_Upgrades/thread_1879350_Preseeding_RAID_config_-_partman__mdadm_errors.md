---
title: "Preseeding RAID config - partman / mdadm errors"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by djsephiroth on 2011-11-11
[SIZE="4"]Technical notes:[/SIZE]
Ubuntu server 10.04.3, i386
The production machine will be an HP ProLiant MicroServer with 8GB of RAM and two 60GB SSDs.
Right now I am testing everything in VirtualBox 4.1.2, using two 8GB static VDIs (partition sizes adjusted accordingly). 

[SIZE="4"]What I am trying to accomplish:[/SIZE]

I'm using a preseed file to automate an unattended installation for a database server. (I have over a hundred machines, so setting up the systems individually introduces more potential issues and loss of time than I'd like.) 

I have made two alterations to the ISO; adding a "microserver.preseed" and adding an entry for this preseed to the main menu. I then boot my VM using this ISO; eventually the production machine will boot the same ISO. 

The preseed file selects typical or default settings (US local/layout, DHCP, ) up until the time it gets to partitioning the drives, at which point it uses partman-auto recipes to set up the drives as follows:

The MD devices (did anyone else think of Ender's Game upon first seeing that phrase?) are all RAID1 between partitions on the SSDs. 

```
md0, 4GB, sda1/sdb1	/
md1, 16GB, sda2/sdb2			/usr
md2, 5GB, sda3/sdb3			/tmp
md3, 30GB, sda5/sdb5			/var
md4, 5.02GB, sda6/sdb6		/home
```

There is no swap file, as we have 8GB of memory in the production machine.

While the above scheme is what will be used in production, I have set all the partitions to 1GB simply for testing in the VM (and since I don't want to make two 60GB static VDIs).

Here's the relevant portion of the preseed file:
```
partman-base partman/exception_handler_note note
d-i partman/default_filesystem string ext4
d-i partman-md/device_remove_md boolean true
d-i partman/alignment select cylinder
d-i partman-auto/method string raid
d-i partman-auto/disk string /dev/sda /dev/sdb
d-i partman-auto/expert_recipe string \
      multiraid ::                                         \
              1000 1000 1000 raid                          \
                      $primary{ } method{ raid }           \
              .                                            \
              1001 1001 1001 raid                          \
                      $primary{ } method{ raid }           \
              .                                            \
              1002 1002 1002 raid                          \
                      $primary{ } method{ raid }           \
              .                                            \
              1003 1003 1003 raid                          \
                      method{ raid }                       \
              .                                            \
              1004 1004 1004 raid                          \
                      method{ raid }                       \
              .
d-i partman-auto-raid/recipe string                        \
    1 2 0 ext4 /                                           \
        /dev/sda1#/dev/sdb1                                \
    .                                                      \
    1 2 0 ext4 /usr                                        \
        /dev/sda2#/dev/sdb2                                \
    .                                                      \
    1 2 0 ext4 /tmp                                        \
        /dev/sda3#/dev/sdb3                                \
    .                                                      \
    1 2 0 ext4 /var                                        \
        /dev/sda4#/dev/sdb5                                \
    .                                                      \
    1 2 0 ext4 /home                                       \
        /dev/sda5#/dev/sdb6                                \
    .
d-i partman-md/confirm_nooverwrite boolean true
d-i partman-md/confirm boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
``` 

[SIZE="4"]What is happening:[/SIZE]

Everything goes smoothly until partway into the RAID configuration. I receive a red error screen which instructs me to check the logs and/or the fourth tty. Upon viewing the logs and such, I can see a wall of ```
can't open /var/lib/partman/outfifo: no such file
```

It also appears that the first three partitions are created, but that the next one fails to be created because of an error along the lines of ```
mdadm: /dev/sda3 is too small: 1K
```

Any help is of course appreciated.

I have one machine set up more or less like how I want all the others to be configured. Here's some output from it:

```
$ sudo fdisk -l 

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         487     3905536   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sda2             487        2432    15625216   fd  Linux raid autodetect
/dev/sda3            2432        3040     4882432   fd  Linux raid autodetect
/dev/sda4            3040        7298    34199553    5  Extended
/dev/sda5            3040        6687    29295616   fd  Linux raid autodetect
/dev/sda6            6687        7298     4902912   fd  Linux raid autodetect

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007c544

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         487     3905536   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2             487        2432    15625216   fd  Linux raid autodetect
/dev/sdb3            2432        3040     4882432   fd  Linux raid autodetect
/dev/sdb4            3040        7298    34199553    5  Extended
/dev/sdb5            3040        6687    29295616   fd  Linux raid autodetect
/dev/sdb6            6687        7298     4902912   fd  Linux raid autodetect

Disk /dev/md4: 5020 MB, 5020516352 bytes
2 heads, 4 sectors/track, 1225712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md4 doesn't contain a valid partition table

Disk /dev/md0: 3999 MB, 3999203328 bytes
2 heads, 4 sectors/track, 976368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 16.0 GB, 16000155648 bytes
2 heads, 4 sectors/track, 3906288 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md3: 30.0 GB, 29998645248 bytes
2 heads, 4 sectors/track, 7323888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md2: 4999 MB, 4999544832 bytes
2 heads, 4 sectors/track, 1220592 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

```


```
$ sudo mdadm --detail --scan
ARRAY /dev/md4 level=raid1 num-devices=2 metadata=00.90 UUID=8d1eaa6a:299b1b52:f01f891c:ac71e2af
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=e0b6a897:80779d06:50275e4a:daf38b8b
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=00.90 UUID=d2087ae1:117a22b1:a9973518:ca7dfc0f
ARRAY /dev/md3 level=raid1 num-devices=2 metadata=00.90 UUID=32d49a8a:f9fc6d3f:4798c41b:9b6dbd9a
ARRAY /dev/md2 level=raid1 num-devices=2 metadata=00.90 UUID=dac5a4df:12258ee0:d67da04f:39642626
```

```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0               3844088    351932   3296884  10% /
none                   4062956       236   4062720   1% /dev
none                   4067308         0   4067308   0% /dev/shm
none                   4067308        52   4067256   1% /var/run
none                   4067308         0   4067308   0% /var/lock
none                   4067308         0   4067308   0% /lib/init/rw
/dev/md2               4805696    828796   3732784  19% /tmp
/dev/md3              28835772    442256  26928740   2% /var
/dev/md4               4825872    153452   4427280   4% /home
/dev/md1              15379792    727088  13871448   5% /usr
```

If there is a better way to approach this situation (e.g., cloning the partitioning and RAID config from the example machine to the production boxen, then having the preseed simply select where to mount the filesystems during setup), I am open to whatever is most expedient and efficient. Thanks again for reading this wall of text.

EDIT: pretty pictures!

[https://imgur.com/a/8JHz2](https://imgur.com/a/8JHz2)

[IMG]http://i.imgur.com/15VPI.png[/IMG]
[IMG]http://i.imgur.com/J5Glw.png[/IMG]

---

### Post by djsephiroth on 2011-11-11
More mysteries; here's what happens when I boot into Puppy and run GParted immediately afterward.

[IMG]http://i.imgur.com/Zfepc.png[/IMG]

The RAID and its constituent partitions seem to be created correctly, while the filesystems are never written to them.

Note that sda6 scarfs up the rest of the disk space, though it was explicitly told (afaik) to be 1GB in the recipe above. If someone can link me to - or otherwise provide - a definitive explanation of what the three numbers in a partman-auto recipe mean, it would be most appreciated.

---

### Post by djsephiroth on 2011-11-11
Upon further inspection, I noticed a typo in the preseed file which caused partman to try to mount the extended partition. :B

This of course won't work, as the extended partition is just a wrapper for the logical partitions. This explains the "too small: 1K" error.

Now that this is fixed, all I need to do is find a way to suppress the warning about having no swap partition, as well as the confirmation to create the RAID.

---

