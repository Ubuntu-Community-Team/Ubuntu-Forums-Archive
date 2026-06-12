---
title: "Recommendations for Pentium 4"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by numer248 on 2014-01-14
Im recently bought a used tower. Its a few years old and the previous owner installed xubuntu on it. Im not a fan of xubuntu and have had a few issues getting certain things working on it (it also lags from time to time, but I have a feeling thats due to the hardware). As a result I've begun contemplating installing ubuntu 12.04LTS on it. The only reason I havent tried installing it yet is because I'm worried the current tower set up may not be sufficient to allow ubuntu to run smoothly without lags. Ive included some of the specifics below and would like to request some of you fellow experts and long time users on what would be most appropriate distribution to install, based on the current hardware. FYI, I plan on using the tower for simpling things like browsing the internet (I usually have multiple tabs open), watching videos, and word processing. Any input is greatly appreciated!

**$ cat /proc/cpuinfo**
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping    : 1
microcode    : 0x9
cpu MHz        : 3066.530
cache size    : 1024 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid xtpr
bogomips    : 6133.06
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:
[B]
$ free -m[/B]
             total       used       free     shared    buffers     cached
Mem:           993        833        159          0         74        411
-/+ buffers/cache:        348        644
Swap:         1011          0       1011
**$ uname -m**
i686
**$ getconf LONG_BIT**
32
**$ df -h**
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       146G  7.5G  131G   6% /
udev            489M  4.0K  489M   1% /dev
tmpfs           199M  784K  198M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            497M  4.0K  497M   1% /run/shm
none            100M  8.0K  100M   1% /run/user
**$ cat /proc/meminfo**
MemTotal:        1016912 kB
MemFree:          163304 kB
Buffers:           75960 kB
Cached:           421052 kB
SwapCached:            0 kB
Active:           405224 kB
Inactive:         374144 kB
Active(anon):     288808 kB
Inactive(anon):    94608 kB
Active(file):     116416 kB
Inactive(file):   279536 kB
Unevictable:       31108 kB
Mlocked:           31108 kB
HighTotal:        124912 kB
HighFree:           1656 kB
LowTotal:         892000 kB
LowFree:          161648 kB
SwapTotal:       1036284 kB
SwapFree:        1036284 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        313436 kB
Mapped:            83820 kB
Shmem:             95272 kB
Slab:              23340 kB
SReclaimable:      13100 kB
SUnreclaim:        10240 kB
KernelStack:        2560 kB
PageTables:         5160 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1544740 kB
Committed_AS:    1694028 kB
VmallocTotal:     122880 kB
VmallocUsed:       12600 kB
VmallocChunk:     108216 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       24568 kB
DirectMap2M:      888832 kB

---

### Post by mörgæs on 2014-01-15
Hi, welcome to the fora.

You didn't mention the most important part: The screen card. Anyway, a Pentium 4 with 1 GB memory would be happy with Lubuntu.

---

### Post by Topsiho on 2014-01-15
+1. I quite agree with mörgæs. I even think he is a bit pessimistic. I have a computer here with a Pentium processor, 1 GiB of RAM, and an old AGP-card, on which I installed Ubuntu 12.04. It is fast enough, but with Lubuntu it would be snappier, I suppose. THE limitation is the AGP-card, I think (e.g. can not shrink the icons in the starter to a more decent size).

Topsiho

---

### Post by mastablasta on 2014-01-15
lubuntu for faster experience. you can use ram and system resources for running programs instead of to run nice interface...

---

### Post by numer248 on 2014-01-15
Thank you for the responses and suggestions. I'll give lubuntu a try in that case. For the curious and those that care, the graphics car is an Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04).

---

### Post by mörgæs on 2014-01-15
It's an OK card which works in Lubuntu 13.10 without any special settings.
Please mark the thread 'solved'.

---

