---
title: "Natty Narwhal Unity won't work"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Moyamo on 2011-05-01
I just upgraded to Natty Narwhal. When I first logged in a pop-up dialogue appeared saying that my computer did not fulfil the   hardware requirements to run Unity. 

That cannot be possible this is the output of the lscpu command:

```
Architecture:          i686
CPU op-mode(s):        32-bit
CPU(s):                2
Thread(s) per core:    2
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            15
Model:                 3
Stepping:              4
CPU MHz:               2999.900
L1d cache:             16K
L2 cache:              1024K

```

This is is the output of the free command:

```
             total       used       free     shared    buffers     cached
Mem:       1251612     916332     335280          0      74220     383576
-/+ buffers/cache:     458536     793076
Swap:       860156          0     860156

```

Summarized that is:

Pentium 4 3GHz core running two threads
1.2GB of ram

---

### Post by awam66 on 2011-05-01
You need to tell us what your graphic card is, since it is that that determines whether unity will run.

---

### Post by Moyamo on 2011-05-01
Thanks for such a quick response.

That makes sense. I don't have one. Isn't there a way to use your processor as a graphics card?

---

