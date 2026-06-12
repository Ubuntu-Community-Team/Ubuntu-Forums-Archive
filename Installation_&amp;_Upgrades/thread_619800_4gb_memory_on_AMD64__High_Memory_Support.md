---
title: "4gb memory on AMD64 : High Memory Support"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2007-11-21
Hi,

I've Gutsy Gibbon on AMD64 on Asus Motherboard - M2N-SLI Deluxe.
I've been having 2GB of RAM and today I upgraded to 4GB [ thanks to
thanksgiving sale :) ]

I read the threads [here]("http://ubuntuforums.org/showthread.php?t=510561"), [here]("http://ubuntuforums.org/showthread.php?t=124655&page=3") and [here]("http://ubuntuforums.org/showthread.php?t=609574"). What should I do to enable 
high-memory / 4GB ? Please advice.

```

httproot@shankar-desktop:/boot# free
             total       used       free     shared    buffers     cached
Mem:       4058252     821868    3236384          0      15516     333428
-/+ buffers/cache:     472924    3585328
Swap:       730916          0     730916

root@shankar-desktop:/boot# cat /proc/meminfo 
MemTotal:      4058252 kB
MemFree:       3234512 kB
Buffers:         15524 kB
Cached:         333432 kB
SwapCached:          0 kB
Active:         490444 kB
Inactive:       229344 kB
SwapTotal:      730916 kB
SwapFree:       730916 kB
Dirty:              48 kB
Writeback:           0 kB
AnonPages:      370736 kB
Mapped:          99396 kB
Slab:            32884 kB
SReclaimable:    16236 kB
SUnreclaim:      16648 kB
PageTables:      19632 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2760040 kB
Committed_AS:  1054452 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     27200 kB
VmallocChunk: 34359711115 kB

root@shankar-desktop:/boot# grep -i smp config-2.6.22-14-generic 
CONFIG_SMP=y
CONFIG_SUSPEND_SMP=y
# CONFIG_X86_VSMP is not set

root@shankar-desktop:/boot#  grep -i highmem config-2.6.22-14-generic 
root@shankar-desktop:/boot# 

```

---

### Post by angryfirelord on 2007-11-21
It looks like it's already enabled because when you ran *free*, you got:
```
           total
Mem:       4058252
```
Unless you mean something different, Ubuntu 64-bit can see all 4GB of RAM.

You can also run System Monitor to double-check as well.

---

