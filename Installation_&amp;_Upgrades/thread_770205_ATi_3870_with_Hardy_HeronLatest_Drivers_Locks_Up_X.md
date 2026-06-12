---
title: "ATi 3870 with Hardy Heron/Latest Drivers Locks Up X"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by kingtaurus on 2008-04-27
Hi,

I've installed Hardy Heron on my new desktop. Specs:
Intel Core 2 Q9450 (Stock speeds)
4GB of DDR2 Memory (G-Skill PC2 8500)
Asus P5K-E/Wifi-AP
HIS 3870 (AMD/ATI 3870)

If I tried to enable or install the ATi binary driver and attempt to use an Xgl server or X server (using AIGLX). I get a full lock of the system (no kernel panic, Alt-SysRq-<keystroke> has no affect, <Ctrl>-<Alt>-<Backspace or Delete> has no affect, ...)

I've tried using the hardy restricted driver package, envyng builds (8.3 ATi driver), and the 8.4 driver installer. In the Xorg logs, I get the following (which looks like the xorg.conf is getting the wrong configuration)... the warnings from the log file are below

```

(WW) RADEON(0): Failed to set up write-combining range (0xd0000000,0x10000000)
..
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
...
(II) AIGLX: Screen 0 is not DRI capable

```

---

### Post by sayems on 2008-04-28
"sudu apt-get remove xorg-driver-fglrx"

---

### Post by kingtaurus on 2008-04-28
Thanks for the reply.

I've done that. Currently, I'm using the vesa instead fglrx. I think I may have found another thread that might have the solution (it looks like mtrr is not being setup properly). [Re: HD3850, ATI drivers and Hardy]("http://ubuntuforums.org/showthread.php?t=768426&page=2")

---

### Post by kingtaurus on 2008-04-29
I think there is a bug when using 4GB of memory and an ASUS motherboard with memory remapping enabled. If I disable it, I can use the fglrx drivers, and I'm getting (awesome fps from glxgears): 
```

gking@bender:~$ glxgears 
53864 frames in 5.0 seconds = 10772.776 FPS
54057 frames in 5.0 seconds = 10811.272 FPS

```

further,
```

gking@bender:/etc/X11$ cat /proc/meminfo 
MemTotal:      3355540 kB
MemFree:       2068500 kB
Buffers:          4044 kB
Cached:         604932 kB
SwapCached:          0 kB
Active:         695972 kB
Inactive:       336824 kB
SwapTotal:     8000328 kB
SwapFree:      8000328 kB
Dirty:             112 kB
Writeback:           0 kB
AnonPages:      423876 kB
Mapped:          91144 kB
Slab:            63700 kB
SReclaimable:    45944 kB
SUnreclaim:      17756 kB
PageTables:      16008 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   9678096 kB
Committed_AS:   880996 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     41952 kB
VmallocChunk: 34359696351 kB

```

Further, mtrr shows all being write-back:
```

gking@bender:/etc/X11$ cat /proc/mtrr 
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 256MB: write-back, count=1

```

I got this solution from this thread:
[http://ubuntuforums.org/showthread.php?t=768426&page=2](http://ubuntuforums.org/showthread.php?t=768426&page=2)

However, I don't have access to the entire amount of system memory.


When memory remapping is enabled - it looks like this ...
```

reg00: base=0xd0000000 (3328MB), size= 256MB: uncachable, count=1
reg01: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
reg02: base=0x00000000 (   0MB), size=4096MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size= 512MB: write-back, count=1
reg04: base=0x120000000 (4608MB), size= 256MB: write-back, count=1

```

---

### Post by kingtaurus on 2008-04-29
I've submitted this to lauchpad as a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/224404]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/224404")

---

