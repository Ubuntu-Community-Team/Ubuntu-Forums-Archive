---
title: "Cannot mount raid partition after upgrade to 10.04"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by gynormo on 2010-06-06
Hello,

I've run into a particularly puzzling situation. Yesterday afternoon I completed the upgrade process to 10.04, from Karmic. Upon doing the final reboot and re-entering my desktop, my 1TB storage partition won't mount. This is baaaad!

The Error:
```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/mapper/nvidia_dfidadjd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Dmesg output:
```
[   68.308919] end_request: I/O error, dev fd0, sector 0
[   87.002516] Clocksource tsc unstable (delta = -221139314 ns)
[   87.884238] EXT3-fs error (device dm-1): ext3_check_descriptors: Block bitmap for group 384 not in group (block 0)!
[   87.900264] EXT3-fs: group descriptors corrupted!
[  586.582964] EXT3-fs error (device dm-1): ext3_check_descriptors: Block bitmap for group 384 not in group (block 0)!
[  586.600255] EXT3-fs: group descriptors corrupted!
[  914.370437] EXT2-fs error (device dm-1): ext2_check_descriptors: Block bitmap for group 384 not in group (block 0)!
[  914.370452] EXT2-fs: group descriptors corrupted!
[ 1064.220217] EXT2-fs error (device dm-1): ext2_check_descriptors: Block bitmap for group 384 not in group (block 0)!
[ 1064.220232] EXT2-fs: group descriptors corrupted!

```

I've scoured around a bit for any solution pertaining to that error message, but I haven't come across any solutions for my particular dmesg output. I can grab any extra info that might help us out further.

I apologize if this is the wrong forum, I *think* I'm in the right spot!

Any insights would be greatly appreciated :(

---

### Post by bildr on 2010-06-06
have you tried this with only one disk plugged in? note: only one disk so if something borks you still have a good image to work with.

[http://www.linuxquestions.org/questions/linux-general-1/raid1-fixing-a-corrupted-file-system-699224/](http://www.linuxquestions.org/questions/linux-general-1/raid1-fixing-a-corrupted-file-system-699224/)

---

### Post by gynormo on 2010-06-06
I run into problems right off the bat with that solution, as the partition itself looks a tad pooched. I'm a tad rusty on the linux side here, so further digging on my own is a little limited!

```
eric@ubuntu:~$ sudo mke2fs -n /dev/sda1
mke2fs 1.41.11 (14-Mar-2010)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```

Gparted information for /dev/sda1 gives me a warning:

```
e2label: No such file or directory while trying to open /dev/sda1 Couldn't find valid filesystem superblock.

dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: No such file or directory while trying to open /dev/sda1
```

I only have the one partition on the disk.

---

### Post by bildr on 2010-06-06
what does df give you?

this is one reason I don't like the abstraction of partitions and logical volumes, it becomes a pain to see what composes each.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) should have most of what you need, just look at the testing section

mdadm is the utility to be playing with.

make sure one of your raid volumes is disconnected, you can lose ALL data doing this wrong.

---

### Post by gynormo on 2010-06-06
I went in via the 9.10 livecd and ran the check disk function through gparted.

Did the trick. I'll plug in my other drive, should be good to go. Very weird, I wonder why the upgrade mucked it up. Oh well.

Thanks for your help!!

---

### Post by manus_eiffel on 2010-10-07
Can you provide the exact steps you have performed to get the raid working again? I'm having the same problem but I'm not sure what you mean by check disk and the disk that needs to be removed and put back.

---

### Post by manus_eiffel on 2010-10-11
Answering to myself as I was able to fix my raid array easily without changing much.

I used the blkid command which helped me figured out what was  wrong. Before ubuntu 10.04 my raid was /dev/sda1 to /dev/sdd1 and my  root partition was /dev/sde1. After the upgrade, looks like that my  /dev/sde1 was now known as /dev/sda1 and all the names had been shifted thus making my raid description invalid.

I edited my mdadm.conf file and manually specified the DEVICES to their new names and  enumerated them again in the ARRAY line. After that it booted just fine.

---

