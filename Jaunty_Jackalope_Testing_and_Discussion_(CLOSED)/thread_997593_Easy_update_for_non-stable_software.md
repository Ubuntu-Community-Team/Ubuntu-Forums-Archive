---
title: "Easy update for non-stable software"
date: 2008-11-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mencargo on 2008-11-30
Since we are in Apha OS, I was wondering if there's a special repository with beta software like Firefox 3.1, 2.6.28 Kernel, ...
So that I could search this packages with apt-get/aptitude?

Or any other easy way to update from beta versions?

---

### Post by Neon Lights on 2008-11-30
I think after the UDS in december, all the apps expected to be in jaunty will be pushed into the repos for testing. :]

---

### Post by ronacc on 2008-11-30
for firefox3.1 add this PPA to your sources.list .
```
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
deb-src http://ppa.launchpad.net/fta/ubuntu jaunty main
```
the 2.6.28 kernel is in synaptic just not the metapackage , just install it and its headders, you may have to hand update your video driver since the metapackage is missing , I use nvidia and I did have to , I'm not sure about ATI.

---

### Post by ccw on 2008-11-30
> **mencargo said:**
> Since we are in Apha OS, I was wondering if there's a special repository with beta software like Firefox 3.1, 2.6.28 Kernel, ...
So that I could search this packages with apt-get/aptitude?

Or any other easy way to update from beta versions?

a 2.6.28 kernel is in jaunty already. 
a firefox-3.1 package will be in jaunty universe soon.

---

### Post by scradock on 2008-11-30
> **ronacc said:**
> 
the 2.6.28 kernel is in synaptic just not the metapackage , just install it and its headders, you may have to hand update your video driver since the metapackage is missing , I use nvidia and I did have to , I'm not sure about ATI.

I'm using the 2.6.28 kernel with no "modules" packages, and no headers. The OSS radeon/ati drivers work fine, and compiz works without any fuss. Haven't tried the fglrx driver from ATI - haven't needed to since early in Intrepid testing.

---

### Post by zika on 2008-12-01
> Haven't tried the fglrx driver from ATI - haven't needed to since early in Intrepid testing.

Which driver are You using if not fglrx (Mobility Radeon HD 3600 Series, Intrepid 64)?

---

### Post by scradock on 2008-12-01
As I said, the open-source radeon/ati drivers. They install as xserver-xorg-video-ati and xserver-xorg-video-radeon, versions 1:6.9.0+git20081. No fglrx driver anywhere.

---

### Post by zika on 2008-12-02
> **scradock said:**
> As I said, the open-source radeon/ati drivers. They install as xserver-xorg-video-ati and xserver-xorg-video-radeon, versions 1:6.9.0+git20081. No fglrx driver anywhere.

I have:ATI Mobility Radeon HD 3600 Series

I am not sure if I can use that driver.

If I can, what are pros and cons fro using that driver instead fglrx ...? I do not play games ...

---

### Post by zika on 2008-12-02
As TeX would say: I'm stummied

I've just checked:

xserver-xorg-video-ati:installed:1:6.9.0+git20081
xserver-xorg-video-radeon:installed:1:6.9.0+git20081
xorg-driver-fglrx:installed

OS:Intrepid Ibex Ubuntu 8.10 Amd_64

Without ATI fglrx driver I would't have Compiz or even X?

---

### Post by scradock on 2008-12-03
> **zika said:**
> As TeX would say: I'm stummied

I've just checked:

xserver-xorg-video-ati:installed:1:6.9.0+git20081
xserver-xorg-video-radeon:installed:1:6.9.0+git20081
xorg-driver-fglrx:installed

OS:Intrepid Ibex Ubuntu 8.10 Amd_64

Without ATI fglrx driver I would't have Compiz or even X?

OK, so you have those drivers installed. Have you tried removing fglrx? You can do that through the Hardware Drivers utility - and it's easy to reverse if you don't like the result. I suspect that the radeon driver isn't going to be adequate for your card - it's much newer than mine. Maybe the radeonhd driver would work (instead of radeon) - that would make sense since you have an HD card. 

Even if the OS drivers don't support Compiz, your system should fall back to the mesa driver and allow X to run.

You would need to ask in the Laptop and hardware forum to get more knowledgeable people commenting on the HD3600 drivers.

---

### Post by zika on 2008-12-03
> **scradock said:**
> OK, so you have those drivers installed. Have you tried removing fglrx? You can do that through the Hardware Drivers utility - and it's easy to reverse if you don't like the result. I suspect that the radeon driver isn't going to be adequate for your card - it's much newer than mine. Maybe the radeonhd driver would work (instead of radeon) - that would make sense since you have an HD card. 

Even if the OS drivers don't support Compiz, your system should fall back to the mesa driver and allow X to run.

You would need to ask in the Laptop and hardware forum to get more knowledgeable people commenting on the HD3600 drivers.

Cool! Everything works without fglrx. Compiz works  with $compiz --replace$. Thank You!

I think that radeonhd driver is not for my card but I will check again. No, it is not.

There is no flicker in movies eventhough Compiz is running! (Sic! see below) Only the smoothing effects from Catalyst are gone, but that is the small price to pay.

There is a downside, at boot Ubuntu is somewhat struggling now and it takes a bit longer. It seems that kernel has somehow written that it was compiled with fglrx driver present? Is that a problem?

(below): Compiz is not working after reboot. But, nevertheless ... I've learned something ... ;)

---

