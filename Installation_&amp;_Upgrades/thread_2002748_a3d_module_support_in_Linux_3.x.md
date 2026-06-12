---
title: "a3d module support in Linux 3.x?"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by curts on 2012-06-13
I have not been able to get the a3d module to load successfully in the 64-bit versions of Ubuntu 11.04, 11.10, or 12.04.  Executing the command 'sudo modprobe a3d' freezes the system.  Has anyone else been able to make this work?  Is a custom kernel rebuild required to include Assasin 3D joystick support in the Ubuntu Linux 3.2 kernel?

I've tried to research this on-line and have come to the conclusion the a3d module has not been actively supported beyond the Linux 2.6 kernel.  Can anybody confirm this?  This could explain why it works in Ubuntu 10.04 but not the versions built on Linux 3.x.

P.S. I only use 32-bit Ubuntu in VMs, so I've not tested this problem in 32-bit.

---

### Post by curts on 2012-06-28
The gameport has been created by the kernel.  Here is the output from loading the joydump module:
```
[  213.066404] joydump: ,------------------ START ----------------.
[  213.066412] joydump: | Dumping:      pci0000:00:09.0/gameport0 |
[  213.066417] joydump: | Speed:                          854 kHz |
[  213.077250] joydump: >------------------ DATA -----------------<
[  213.077255] joydump: | index:   0 delta:   0 us data: 11111110 |
[  213.077267] joydump: | index:   1 delta:   0 us data: 11111111 |
[  213.077278] joydump: | index:   2 delta: 177 us data: 10011111 |
[  213.077289] joydump: | index:   3 delta:   6 us data: 10001111 |
[  213.077300] joydump: | index:   4 delta:   6 us data: 00011111 |
[  213.077310] joydump: | index:   5 delta:   7 us data: 00001111 |
[  213.077321] joydump: | index:   6 delta:   6 us data: 00011111 |
[  213.077331] joydump: | index:   7 delta:   6 us data: 00001111 |
[  213.077342] joydump: | index:   8 delta:   6 us data: 00011111 |
[  213.077353] joydump: | index:   9 delta:   7 us data: 00001111 |
[  213.077363] joydump: | index:  10 delta:   6 us data: 00011111 |
[  213.077374] joydump: | index:  11 delta:   7 us data: 00001111 |
[  213.077385] joydump: | index:  12 delta:   6 us data: 00011111 |
[  213.077395] joydump: | index:  13 delta:   6 us data: 00001111 |
[  213.077406] joydump: | index:  14 delta:  24 us data: 00011111 |
[  213.077417] joydump: | index:  15 delta:   6 us data: 00001111 |
[  213.077427] joydump: | index:  16 delta:   7 us data: 00011111 |
[  213.077438] joydump: | index:  17 delta:   6 us data: 00001111 |
[  213.077448] joydump: | index:  18 delta:   6 us data: 00011111 |
[  213.077459] joydump: | index:  19 delta:   7 us data: 00001111 |
[  213.077470] joydump: | index:  20 delta:   6 us data: 00011111 |
[  213.077480] joydump: | index:  21 delta:   7 us data: 00001111 |
[  213.077491] joydump: | index:  22 delta:   6 us data: 00011111 |
[  213.077502] joydump: | index:  23 delta:   6 us data: 00001111 |
[  213.077512] joydump: | index:  24 delta:   6 us data: 00011111 |
[  213.077523] joydump: | index:  25 delta:   7 us data: 00001111 |
[  213.077533] joydump: | index:  26 delta:   6 us data: 00011111 |
[  213.077544] joydump: | index:  27 delta:  24 us data: 00001111 |
[  213.077555] joydump: | index:  28 delta:   6 us data: 00011111 |
[  213.077565] joydump: | index:  29 delta:   7 us data: 00001111 |
[  213.077576] joydump: | index:  30 delta:   6 us data: 00011111 |
[  213.077586] joydump: | index:  31 delta:   6 us data: 00001111 |
[  213.077597] joydump: | index:  32 delta:   7 us data: 00011111 |
[  213.077608] joydump: | index:  33 delta:   6 us data: 00001111 |
[  213.077618] joydump: | index:  34 delta:   6 us data: 00011111 |
[  213.077629] joydump: | index:  35 delta:   7 us data: 00001111 |
[  213.077639] joydump: | index:  36 delta:   6 us data: 11111111 |
[  213.077650] joydump: | index:  37 delta:   6 us data: 11101111 |
[  213.077661] joydump: | index:  38 delta:   7 us data: 00011111 |
[  213.077671] joydump: | index:  39 delta:   6 us data: 00001111 |
[  213.077682] joydump: | index:  40 delta:  24 us data: 00111111 |
[  213.077692] joydump: | index:  41 delta:   6 us data: 00101111 |
[  213.077703] joydump: | index:  42 delta:   6 us data: 00111111 |
[  213.077714] joydump: | index:  43 delta:   7 us data: 00101111 |
[  213.077724] joydump: | index:  44 delta:   6 us data: 00111111 |
[  213.077735] joydump: | index:  45 delta:   7 us data: 00101111 |
[  213.077746] joydump: | index:  46 delta:   6 us data: 11111111 |
[  213.077756] joydump: | index:  47 delta:   6 us data: 11101111 |
[  213.077767] joydump: | index:  48 delta:   7 us data: 11011111 |
[  213.077778] joydump: | index:  49 delta:   6 us data: 11001111 |
[  213.077788] joydump: | index:  50 delta:   6 us data: 00111111 |
[  213.077799] joydump: | index:  51 delta:   7 us data: 00101111 |
[  213.077809] joydump: | index:  52 delta:   6 us data: 11111111 |
[  213.077820] joydump: | index:  53 delta:  24 us data: 11101111 |
[  213.077831] joydump: | index:  54 delta:   6 us data: 11011111 |
[  213.077841] joydump: | index:  55 delta:   7 us data: 11001111 |
[  213.077852] joydump: | index:  56 delta:   6 us data: 00011111 |
[  213.077863] joydump: | index:  57 delta:   6 us data: 00001111 |
[  213.077873] joydump: | index:  58 delta:   6 us data: 00011111 |
[  213.077884] joydump: | index:  59 delta:   7 us data: 00001111 |
[  213.077894] joydump: | index:  60 delta:   6 us data: 00011111 |
[  213.077905] joydump: | index:  61 delta:   7 us data: 00001111 |
[  213.077916] joydump: | index:  62 delta:   6 us data: 00011111 |
[  213.077926] joydump: | index:  63 delta:   6 us data: 00001111 |
[  213.077937] joydump: | index:  64 delta:   7 us data: 11111111 |
[  213.077947] joydump: | index:  65 delta:   5 us data: 10111111 |
[  213.077958] joydump: | index:  66 delta:  24 us data: 10101111 |
[  213.077969] joydump: | index:  67 delta:   6 us data: 00111111 |
[  213.077979] joydump: | index:  68 delta:   7 us data: 00101111 |
[  213.077990] joydump: | index:  69 delta:   6 us data: 11111111 |
[  213.078001] joydump: | index:  70 delta: 245 us data: 11111110 |
[  213.078011] joydump: `------------------- END -----------------'

```

---

