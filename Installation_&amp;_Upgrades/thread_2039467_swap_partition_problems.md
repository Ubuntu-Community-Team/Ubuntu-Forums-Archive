---
title: "swap partition problems"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by NoReflection on 2012-08-08
Hey guys, I am trying to install Xubuntu on a second hard drive next to windows 7. I selected to set up my own partitions for /swap but I don't see a swap in the selection so I manually type in /swap but when I go to install it says I have no swap and it is recommended to have one. Is the swap called something else in xubuntu?

---

### Post by oldfred on 2012-08-08
It is not /swap as it is not a mounted partition that you directly use, but just a empty space tha the system uses to write data into, it is just swap.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by NoReflection on 2012-08-08
I see! thank you. I skimmed threw the info on that link but didn't see where it would have explained its not an actual partition. That has been my confusion the whole time. I don't think I have seen anything where it was fully explained that way.

Thank you again

---

### Post by oldfred on 2012-08-08
It really is a partition but without any format.

Also, if you encrypt your /home, the swap space is also encrypted and just about everything in the system does not see that partition as anything, except it still is a partition. It has UUID and is shown as a device. Actually everything in LInux is a file but that is another distinction. 

This drive is gpt so it shows swap slight differently than a typical list from sudo fdisk.
```
fred@fred-Precise:~$ sudo parted /dev/sdb unit s print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size        File system     Name      Flags
 1      34s        16064s      16031s
 2      16065s     51215219s   51199155s   ext4            MAVERICK
 3      51215220s  57352049s   6136830s    linux-swap(v1)
 4      57352050s  312576704s  255224655s  ext4


```

---

### Post by NoReflection on 2012-08-08
ok, now that you explain it that way "partition with out any format" that makes me feel better. Because It has always been referred to as a partition. 

would it be better to use ext4 instead of 3?

---

### Post by oldfred on 2012-08-09
Swap has no format or file system.

I find ext4 better for / (root). My old data partition is still ext3, but if I was creating it today I would use ext4.

---

