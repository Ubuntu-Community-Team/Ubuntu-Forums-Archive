---
title: "NVidia 330M: random freezes with 195.30 not 190.53 driver"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by appultaart on 2010-03-14
Hi all,

I have a Sony Vaio laptop with a NVidia 330M graphics card. This card is very new, it is not yet supported in the official NVidia binary drivers for linux. 

On Karmic 64-bit, I can get this card up and running using the trick described here by editing xorg.conf to point to the EDID-file extracted from Windows ([http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22]("http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22")). 

Running Lucid 64-bit alpha3 (all packages up-to-date), I experience some problems:

1. With the standard packages (I guess, that is the nouveau driver?), my screen resolution is 2048x1560 (i believe?), which is larger than my screen (1920x1080). I cannot see bottom of my desktop, nor the right side, fully. Any attempt to change this (by installing Nvidia driver from Jockey) results in a system freeze, or in a 'low graphics' mode (800x640 px). 

2. Like I did in Karmic, I installed the NVidia binary driver by downloading from Nvidia website (installing binary driver using Jockey did not work, see above). 

3. Both binaries 190.53 and 195.30 from NVidia do not compile on the 2.6.32-16-generic kernel. I get a message like "wrong kernel headers" or something...

4. Both binaries 190.53 and 195.30 do compile and work against the 2.6.32-15-generic kernel. So I stick to this kernel for now.

5. The 190.53 binary driver works good. No problems observed.

6. The 195.30 binary driver causes random freeze of the Gnome environment: I can only use my mouse but there is no keyboard input possible. It blocks the screen, I have to shutdown my laptop by forcing power-off using my Power_off button.

7. In /var/messages/Xorg.0.log.old, this shows (see below). Apparently, the 195.30 compiled kernel module 'nvidia' causes the (X?) server to be stuck in an infinite loop, which renders the system unresponsive.

While it is thus far a nuissance, I thought to report here in case it is of importance to others. It is NVidia's binary drivers, so not much use to file a bug report on Launchpad on this for now, right?

Thanks.

```
[mi] EQ overflowing. The server is probably stuck in an infinite loop.

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a25e8]
1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a1e64]
2: /usr/bin/X (xf86PostMotionEventP+0xc4) [0x47ca54]
3: /usr/bin/X (xf86PostMotionEvent+0xa9) [0x47cbf9]
4: /usr/lib/xorg/modules/input/wacom_drv.so (0x7f55308c2000+0x7cec) [0x7f55308c9cec]
5: /usr/lib/xorg/modules/input/wacom_drv.so (0x7f55308c2000+0x88c0) [0x7f55308ca8c0]
6: /usr/lib/xorg/modules/input/wacom_drv.so (0x7f55308c2000+0xba5f) [0x7f55308cda5f]
7: /usr/lib/xorg/modules/input/wacom_drv.so (0x7f55308c2000+0x56bc) [0x7f55308c76bc]
8: /usr/lib/xorg/modules/input/wacom_drv.so (0x7f55308c2000+0x43c3) [0x7f55308c63c3]
9: /usr/bin/X (0x400000+0x6f917) [0x46f917]
10: /usr/bin/X (0x400000+0x11c553) [0x51c553]
11: /lib/libpthread.so.0 (0x7f55365aa000+0xf920) [0x7f55365b9920]
12: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f553131e000+0x72a3d) [0x7f5531390a3d]
13: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f553131e000+0x7340f) [0x7f553139140f]
14: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f553131e000+0xce15a) [0x7f55313ec15a]
15: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f553131e000+0x32b279) [0x7f5531649279]
16: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f553131e000+0x32bac5) [0x7f5531649ac5]
17: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f553131e000+0x32bc64) [0x7f5531649c64]
18: /usr/bin/X (0x400000+0xd9778) [0x4d9778]
19: /usr/bin/X (0x400000+0xb18d9) [0x4b18d9]
20: /usr/bin/X (0x400000+0xb2aed) [0x4b2aed]
21: /usr/bin/X (0x400000+0x30bdc) [0x430bdc]
22: /usr/bin/X (0x400000+0x2613a) [0x42613a]
23: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f55352a3c4d]
24: /usr/bin/X (0x400000+0x25ce9) [0x425ce9]
```

---

### Post by Seventh Reign on 2010-03-14
Nothing new.  This is about as common as Rain in the Amazon.

---

