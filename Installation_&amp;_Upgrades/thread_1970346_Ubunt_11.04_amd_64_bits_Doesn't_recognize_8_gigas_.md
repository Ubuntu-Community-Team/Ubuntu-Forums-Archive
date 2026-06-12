---
title: "Ubunt 11.04 amd_64 bits Doesn't recognize 8 gigas RAM"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by kaniko on 2012-05-01
Hello, I've installed Ubuntu 11.04 64 bits

$ uname -a 


Linux MyComputer 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

$ free -m 

total used free shared buffers cached
Mem: 3646 3574 72 0 107 1732
-/+ buffers/cache: 1733 1913
Swap: 1950 0 1950


$ sudo lshw -C memory


*-memory
description: System Memory
physical id: 1000
slot: System board or motherboard
size: 8GiB


I don't know what is the problem, Could anybody help me. I searched a lot, but with the Ubuntu 64 bits it shouldn't be a problem to recognize 8 gigas RAM

Thanks in advance

---

