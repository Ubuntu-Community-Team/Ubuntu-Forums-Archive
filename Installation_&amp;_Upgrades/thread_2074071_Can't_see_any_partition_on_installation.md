---
title: "Can't see any partition on installation"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by mogeb on 2012-10-20
Hello everyone,
I am trying to install Ubuntu 12.04 (x86_64) on my new Dell Inspiron 15R Special Edition (Inspiron 7520).

I can boot from the live CD, and pass the first steps. The problem is, when I have to choose the partition on which I want to install Ubuntu, I can't see any partition.
If I decide to just try Ubuntu instead of installing it, I can perfectly see the other partitions using gparted, or fdisk -l.

Any help would be appreciated.
Thanks.

---

### Post by funicorn on 2012-10-20
Usually this means you are using GPT partition table, or there is something with your partition table. It's can be told from the output of parted, paste the result of following command

*sudo parted /dev/sda print*

---

### Post by mogeb on 2012-10-20
Thank you for your answer.
Here is the result of the command:

```

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  25.0GB  24.9GB  primary  ntfs         boot
 3      25.0GB  790GB   766GB   primary  ntfs
 4      790GB   1000GB  210GB   primary  ext4

```

Partition number 4 is the partition I created (I formated it using gparted).
I would also like to add that i already erased the GPT partition table using the steps described on this page: [http://blog.paulgu.com/windows/delete-gpt-protective-partition/](http://blog.paulgu.com/windows/delete-gpt-protective-partition/)

Thank you

---

### Post by mogeb on 2012-10-20
Ok I finally got it to work. I tried installing Fedora 17 (sorry everyone :P) because I know I read somewhere that it was "GPT-compatible". While booting into it I got the following message:

Disks sda, sdb contain BIOS RAID metadata, but are not part of any recognized BIOS RAID sets. Ignoring disks sda, sdb.

So I ran the following command to erase the metada:
sudo dmraid -r -E /dev/sda

And I can now install Ubuntu! 
Thanks for your help and I hope this helps other people.

---

