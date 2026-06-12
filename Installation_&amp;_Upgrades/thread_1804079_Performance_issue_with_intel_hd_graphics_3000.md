---
title: "Performance issue with intel hd graphics 3000"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by sir83 on 2011-07-14
Hi,

I have just bought me a htpc.

Hardware:
Mainboard: Zotac H67ITX-C-E
CPU: Intel Core i5 2405s (with Intel HD Graphics 3000)

I've tried to follow some guides I have found, but I still have som issues with the video performance. When a video is panning or changing rapidly, the graphics can't keep up. I see it as horizontal fractures in the picture.

I try to use the hardware accelerator in the GPU, but I don't know if I'm doing that.

I updated the kernel because I read that it could help:
uname -r
> 2.6.39-020639rc4-generic

I'm also using the xorg-edgers repository:
> [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main

Here is my vainfo:
> libva: libva version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: i965 Driver 0.1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

Here is my glxinfo output: [http://pastebin.com/kAT6S0GQ](http://pastebin.com/kAT6S0GQ)
Here is my dmesg output: [http://pastebin.com/D5Ara1QC](http://pastebin.com/D5Ara1QC)

I've tried to use the [mplayer-vaapi]("http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/"), but I cant see any difference.


I may have messed up my configuration because I have tried to follow many guides that I have found. Non of them seems to work.

Could someone help me here? Just ask if should post more information.

---

### Post by dino99 on 2011-07-14
you cant get the same performance with an embedded chip with low specs, compared to a dedicated graphic card. For video streaming only use small window, here the best drivers cant do miracles.

[http://askubuntu.com/questions/39527/poor-performance-with-intel-hd-3000-gpu](http://askubuntu.com/questions/39527/poor-performance-with-intel-hd-3000-gpu)
[https://secure.wikimedia.org/wikipedia/en/wiki/Intel_GMA](https://secure.wikimedia.org/wikipedia/en/wiki/Intel_GMA)

---

### Post by sir83 on 2011-07-14
> **dino99 said:**
> you cant get the same performance with an embedded chip with low specs, compared to a dedicated graphic card. For video streaming only use small window, here the best drivers cant do miracles.

[http://askubuntu.com/questions/39527/poor-performance-with-intel-hd-3000-gpu](http://askubuntu.com/questions/39527/poor-performance-with-intel-hd-3000-gpu)
[https://secure.wikimedia.org/wikipedia/en/wiki/Intel_GMA](https://secure.wikimedia.org/wikipedia/en/wiki/Intel_GMA)

This embedded GPU should be able to use hardware acceleration. If you lookup HD Graphics 3000 on this [wikipage]("http://en.wikipedia.org/wiki/Intel_GMA#Specifications"), you will see that is has hardware acceleration capabilities. 

I thought that if a GPU has hardware acceleration, it could play and scale all supported video formats flawlessly. Isn't that correct?

---

