---
title: "HIGHMEM64G option in 2.6.27-7-server kernel"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by old_one on 2008-11-05
Hello all how's the day treeting you so far? 
Hope I am not in the wrong section.
I have installed the 32bit desktop version initially only to realize that it does not support more then ~4gb of memory. Not so good for my 6gb VmWare testing  box ;)

I have since tried to install the 32bit server versino since it has the HIGHMEM64G compiled but alas my /proc/meminfo still shows only:
 "MemTotal: 3362200 kB"

I checked the config file for the server kernel:
```
grep HIGHMEM /boot/config-2.6.27-7-server
# CONFIG_DEBUG_HIGHMEM is not set
CONFIG_HIGHMEM=y
# CONFIG_NOHIGHMEM is not set
# CONFIG_HIGHMEM4G is not set
CONFIG_HIGHMEM64G=y

``` 
and the uname output:
```
uname -r
2.6.27-7-server

```

The procedure I used to install was to simply go to aptitute and select the linux-server package. Right now I have this installed:
```
dpkg -l | grep 2.6. |grep linux
ii  linux-generic                             2.6.27.7.11                                 Complete Generic Linux kernel
ii  linux-headers-2.6.27-4                    2.6.27-4.6                                  Header files related to Linux kernel version
ii  linux-headers-2.6.27-4-generic            2.6.27-4.6                                  Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-7                    2.6.27-7.16                                 Header files related to Linux kernel version
ii  linux-headers-2.6.27-7-generic            2.6.27-7.16                                 Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-7-server             2.6.27-7.16                                 Linux kernel headers for version 2.6.27 on x
ii  linux-headers-generic                     2.6.27.7.11                                 Generic Linux kernel headers
ii  linux-image-2.6.27-4-generic              2.6.27-4.6                                  Linux kernel image for version 2.6.27 on x86
ii  linux-image-2.6.27-7-generic              2.6.27-7.16                                 Linux kernel image for version 2.6.27 on x86
ii  linux-image-2.6.27-7-server               2.6.27-7.16                                 Linux kernel image for version 2.6.27 on x86
ii  linux-image-generic                       2.6.27.7.11                                 Generic Linux kernel image
ii  linux-image-server                        2.6.27.7.11                                 Linux kernel image on Server Equipment.
ii  linux-libc-dev                            2.6.27-7.16                                 Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.27-4-generic 2.6.27-4.5                                  Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-2.6.27-7-generic 2.6.27-7.12                                 Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common           2.6.27-7.12                                 Non-free Linux 2.6.27 modules helper script
ii  linux-restricted-modules-generic          2.6.27.7.11                                 Restricted Linux modules for generic kernels
ii  linux-server                              2.6.27.7.11                                 Complete Linux kernel on Server Equipment.

```
Can anyone see what I did wrong? How can I get Kubuntu to see all my wonderful ram? I would rather not install 64bit version yet. And yes my motherboard can and *should* support more then 4gb of memory.
Thanks in advance.

---

### Post by DataMatrix on 2008-11-14
Unfortunately, I have the same problem with 2.6.24-21-generic, it detects only 3G ram, but BIOS show 4096MB of memory and memtest86 also discovers it that way. I'm going to download the server image now, but I don't intend to upgrade to 64bit because of software support issues. I soon as I find the answer, I'll reply here.

Edit: I've installed the 2.6.24-21-server kernel and memory is detected correctly now.
```

~$ uname -a
Linux pripyat 2.6.24-21-server #1 SMP Wed Oct 22 00:18:13 UTC 2008 i686 GNU/Linux

~$ cat /proc/meminfo 
MemTotal:      4131576 kB
MemFree:       3903264 kB
Buffers:          8100 kB
Cached:         148992 kB
SwapCached:          0 kB
Active:          85092 kB
Inactive:       117788 kB
HighTotal:     3260160 kB
HighFree:      3060024 kB
LowTotal:       871416 kB
LowFree:        843240 kB
SwapTotal:     1461872 kB
SwapFree:      1461872 kB
Dirty:               0 kB
Writeback:           0 kB
AnonPages:       45788 kB
Mapped:          22568 kB
Slab:            15088 kB
SReclaimable:     6892 kB
SUnreclaim:       8196 kB
PageTables:       1968 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   3527660 kB
Committed_AS:   361672 kB
VmallocTotal:   118776 kB
VmallocUsed:      3544 kB
VmallocChunk:   115180 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB

~$ free
             total       used       free     shared    buffers     cached
Mem:       4131576     228700    3902876          0       8180     149064
-/+ buffers/cache:      71456    4060120
Swap:      1461872          0    1461872

```

---

### Post by cariboo on 2008-11-14
@DataMatrix

What software support issues are you running into, as I have been using a 64bit version since 6.04 and have absolutely zero propblems with support.

Jim

---

