---
title: "swap_free: Bad swap file entry"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by markusfarkus on 2007-09-17
I have a machine that randomly stops working on my network.  I get this in the message file


Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 40000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000004
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 40000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000004
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000004
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 last message repeated 6 times
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 40000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 40000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 40000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.040000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000004
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 last message repeated 2 times
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000004
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000001
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 40000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 40000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 10000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 40000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000005
Sep 16 14:45:01 compute-0-1 kernel: [43743747.050000] swap_free: Bad swap file entry 50000005


Does anyone know what the numbers are pointing to?

mjr

---

### Post by dixonp on 2007-09-17
Looks like defectuous hardware (ram, disks, ata/sata cables...). If I were you I would run memtest86.

---

### Post by markusfarkus on 2007-09-17
Currently running that on the system...but it is taking forever with 8 gigs of ram.

---

### Post by dixonp on 2007-09-17
I have seen systems where it took memtest at least 24h to report some errors. So if you don't run it long enough you may incorrectly think your RAM is ok when it's not. I would suggest you let memtest do at least 5-10 passes, or let it run for at least 24-48h (whatever is **longer**).

---

### Post by markusfarkus on 2007-09-18
Still cooking as we speak.  Thanks for the advice...I was going to let it do its thing.

---

