---
title: "Strange glxgears output with Intel card"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-07-30
Hi all,
if I run glxgears I get "incomplete" output without FPS results:
> 1974 frames in 5.0 seconds
1979 frames in 5.0 seconds
1981 frames in 5.0 seconds
1971 frames in 5.0 seconds
1998 frames in 5.0 seconds

My Intel card is:
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
If I do:
```
more /var/log/Xorg.0.log |grep EE
```
I get this module error:
```
(EE) Failed to load module "i810" (module does not exist, 0)
```
Anyway the whole performance of my video card are really far from brilliant, using xserver-xorg-video-intel from Karmic repo.

---

### Post by psyke83 on 2009-07-30
> **dentaku65 said:**
> Hi all,
if I run glxgears I get "incomplete" output without FPS results:
That was done to reduce developers' irritation from people using it as a benchmark tool of any sort.

For example, see:
[http://qa-rockstar.livejournal.com/7869.html](http://qa-rockstar.livejournal.com/7869.html)
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

> If I do:
```
more /var/log/Xorg.0.log |grep EE
```
I get this module error:
```
(EE) Failed to load module "i810" (module does not exist, 0)
```

The i810 driver was the pre-modeset (not KMS) driver for intel, and it no longer exists.

> Anyway the whole performance of my video card are really far from brilliant, using xserver-xorg-video-intel from Karmic repo.

There's a serious issue with UXA and 8xx chipsets: [https://bugs.freedesktop.org/show_bug.cgi?id=22877](https://bugs.freedesktop.org/show_bug.cgi?id=22877)

Also, I notice that 3D performance is roughly halved for my 855GM chipset with the 2.6.31.x series kernels compared to the 2.6.30.x series. Try the [2.6.30.3]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/") mainline kernel.

You should also keep an eye on the recent threads re: metacity causing 100% CPU usage with compiz enabled.

---

### Post by dentaku65 on 2009-07-30
> **psyke83 said:**
> That was done to reduce developers' irritation from people using it as a benchmark tool of any sort.

For example, see:
[http://qa-rockstar.livejournal.com/7869.html](http://qa-rockstar.livejournal.com/7869.html)
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)



The i810 driver was the pre-modeset (not KMS) driver for intel, and it no longer exists.



There's a serious issue with UXA and 8xx chipsets: [https://bugs.freedesktop.org/show_bug.cgi?id=22877](https://bugs.freedesktop.org/show_bug.cgi?id=22877)

Also, I notice that 3D performance is roughly halved for my 855GM chipset with the 2.6.31.x series kernels compared to the 2.6.30.x series. Try the [2.6.30.3]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/") mainline kernel.

You should also keep an eye on the recent threads re: metacity causing 100% CPU usage with compiz enabled.

Thx psyke83, with kernel 2.6.30-3 it is little bit better (at least I can watch youtube videos), but I hope for the next release of the driver...

---

