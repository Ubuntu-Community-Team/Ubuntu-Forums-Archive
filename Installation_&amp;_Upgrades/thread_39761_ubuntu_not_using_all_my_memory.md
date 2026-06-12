---
title: "ubuntu not using all my memory"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by rschlack on 2005-06-06
I have a Dell m300 laptop with 768mb of ram.  Using top I can see that ubuntu is only using 640mb or ram.  How can I get Ubuntu to see the rest of my ram?

Thanks,
Rob

---

### Post by Gtaylor on 2005-06-06
Do a:
```

cat /proc/meminfo

```
And paste what you see in the MemTotal field.

---

### Post by rschlack on 2005-06-06
MemTotal:       636908 kB
MemFree:        390248 kB
Buffers:          5272 kB
Cached:          94988 kB
SwapCached:      66440 kB
Active:         131428 kB
Inactive:        69092 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       636908 kB
LowFree:        390248 kB
SwapTotal:     1164672 kB
SwapFree:      1057996 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:         103332 kB
Slab:            11920 kB
CommitLimit:   1483124 kB
Committed_AS:   375876 kB
PageTables:       1728 kB
VmallocTotal:   393136 kB
VmallocUsed:      5600 kB
VmallocChunk:   387116 kB

---

### Post by bored2k on 2005-06-06
[QUOTE=rschlack]MemTotal:       636908 kB
MemFree:        390248 kB
Buffers:          5272 kB
Cached:          94988 kB
SwapCached:      66440 kB
Active:         131428 kB
Inactive:        69092 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       636908 kB
LowFree:        390248 kB
SwapTotal:     1164672 kB
SwapFree:      1057996 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:         103332 kB
Slab:            11920 kB
CommitLimit:   1483124 kB
Committed_AS:   375876 kB
PageTables:       1728 kB
VmallocTotal:   393136 kB
VmallocUsed:      5600 kB
VmallocChunk:   387116 kB[/QUOTE]
 Try installing linux-686 then rebooting.

---

