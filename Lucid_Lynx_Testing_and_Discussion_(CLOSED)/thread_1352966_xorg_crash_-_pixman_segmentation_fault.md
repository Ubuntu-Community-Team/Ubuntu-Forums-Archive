---
title: "xorg crash - pixman segmentation fault"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SevenMachines on 2009-12-12
X is crashing and sending me to low graphics mode. anyone else have this? nouveau or nvidia both afflicted

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a1f98]
1: /usr/bin/X (0x400000+0x64cb9) [0x464cb9]
2: /lib/libpthread.so.0 (0x7f15d5289000+0xf190) [0x7f15d5298190]
3: /usr/lib/libpixman-1.so.0 (0x7f15d4bed000+0x68c0) [0x7f15d4bf38c0]
4: /usr/lib/libpixman-1.so.0 (0x7f15d4bed000+0x35249) [0x7f15d4c22249]
5: /usr/lib/libpixman-1.so.0 (0x7f15d4bed000+0x2f95b) [0x7f15d4c1c95b]
6: /usr/lib/libpixman-1.so.0 (0x7f15d4bed000+0x376b2) [0x7f15d4c246b2]
7: /usr/lib/libpixman-1.so.0 (0x7f15d4bed000+0x38a20) [0x7f15d4c25a20]
8: /usr/lib/libpixman-1.so.0 (0x7f15d4bed000+0x2f65a) [0x7f15d4c1c65a]
9: /usr/lib/libpixman-1.so.0 (pixman_image_composite+0x17c) [0x7f15d4c1d4bc]
10: /usr/lib/xorg/modules/libfb.so (fbComposite+0x163) [0x7f15cfc4a9e3]
11: /usr/bin/X (0x400000+0xd69d0) [0x4d69d0]
12: /usr/bin/X (0x400000+0x163659) [0x563659]
13: /usr/bin/X (0x400000+0x1637b0) [0x5637b0]
14: /usr/bin/X (0x400000+0xa55f3) [0x4a55f3]
15: /usr/bin/X (ConfigureWindow+0xaa7) [0x4580a7]
16: /usr/bin/X (0x400000+0x2ff07) [0x42ff07]
17: /usr/bin/X (0x400000+0x3092c) [0x43092c]
18: /usr/bin/X (0x400000+0x25f95) [0x425f95]
19: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f15d3f91add]
20: /usr/bin/X (0x400000+0x25b39) [0x425b39]
Segmentation fault at address 0x1ba9d4

Fatal server error:
Caught signal 11 (Segmentation fault). Server aborting

---

### Post by Gina on 2009-12-12
I'm getting segmentation faults running X server too.

---

### Post by dino99 on 2009-12-12
hi sevenmachines,

i'm using vdpau repo and this problem happened, so i changed for your repo and installed your latest 195: first i must remove / purge all nvidia installed packages.

Then xorg start normally. i've seen in synaptic that 195 is recognized as a 190, is that normal ? ( sorry to post here, but concern only karmic, lucid identify 195 as 195)

---

### Post by DougieFresh4U on 2009-12-12
Got low graphics mode with .32.7 kernel and using 'fglrx'. Removed 'fglrx' and all is good.

---

### Post by ranch hand on 2009-12-13
I have developed this segmentation fault.

I have an ATI card.

Is there a bug on this?  I will look in the morning.

Can't boot to that install at all.

DougieFresh4U may have it down, though, I believe I had fglrx running on that one.

I rally am too tired.  better hit the sack

---

