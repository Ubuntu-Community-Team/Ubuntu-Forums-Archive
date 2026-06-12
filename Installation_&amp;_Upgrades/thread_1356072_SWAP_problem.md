---
title: "SWAP problem"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by patricksan on 2009-12-15
Dear All,

I installed 9.10 and the swap is not working.
I read some posts but in my case it does not work.

Some information:

1. First, to see if it is being used:
```

patrick@sanubuntudesktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2937       1082       1855          0         75        667
-/+ buffers/cache:        338       2598
Swap:          902          0        902

```

2. Configuration on fdsik
```
patrick@sanubuntudesktop:~$ sudo fdisk -l

Disk /dev/sda: 74.1 GB, 74088185856 bytes
255 heads, 63 sectors/track, 9007 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d0dfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8892    71424958+  83  Linux
/dev/sda2            8893        9007      923737+   5  Extended
/dev/sda5            8893        9007      923706   82  Linux swap / Solaris

```

3. My configuration on /etc/fstab
```
patrick@sanubuntudesktop:~$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7a8fd6c8-6087-4589-a3bf-110242f29d3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
I'm not using UUID, just because I did some mkswap.


5. I also did some tests like what is described on [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
```
sudo swapoff -a
sudo /sbin/mkswap /dev/sda5
sudo swapon -a
```

6. My meminfo:
```
patrick@sanubuntudesktop:~$ cat /proc/meminfo
MemTotal:        3008000 kB
MemFree:         1897832 kB
Buffers:           78148 kB
Cached:           683744 kB
SwapCached:            0 kB
Active:           539100 kB
Inactive:         509256 kB
Active(anon):     427528 kB
Inactive(anon):       16 kB
Active(file):     111572 kB
Inactive(file):   509240 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2146248 kB
HighFree:        1163492 kB
LowTotal:         861752 kB
LowFree:          734340 kB
SwapTotal:        923696 kB
SwapFree:         923696 kB
Dirty:                72 kB
Writeback:             0 kB
AnonPages:        286460 kB
Mapped:           209148 kB
Slab:              38600 kB
SReclaimable:      29068 kB
SUnreclaim:         9532 kB
PageTables:         9844 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2427696 kB
Committed_AS:    1338832 kB
VmallocTotal:     122880 kB
VmallocUsed:        2548 kB
VmallocChunk:     118496 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB

```


Can somebody give me another direction to solve my problem, please?


Thanks,
Patrick

PS.: I'm running Ubuntu 9.1 on a VM.

---

### Post by darkod on 2009-12-15
Why do you think it's not working, because it says Used=0? That just means you have enough ram to run your tasks there at the moment. Mine swap is used 0 most of the time too (in fact haven't seen it used yet, but I'm not checking all the time).

---

### Post by presence1960 on 2009-12-15
> **darkod said:**
> Why do you think it's not working, because it says Used=0? That just means you have enough ram to run your tasks there at the moment. Mine swap is used 0 most of the time too (in fact haven't seen it used yet, but I'm not checking all the time).

Darko is right. Swap is only used when needed. If RAM is running all your tasks you will rarely see swap used. Another thing to keep in mind is Linux uses memory quite differently than windows does, actually it uses memory much more efficiently than windows.

---

### Post by patricksan on 2009-12-16
You are all right.

I had to stress the box a lot to start to see progress.
So I change the value on:

sudo sysctl vm.swappiness=90

Then I could see it working.

What I also noticed, just to leave it here, there is a difference on 
```
free -m
``` and the System monitor.

Thanks for all help

Best regards,
Patrick

---

