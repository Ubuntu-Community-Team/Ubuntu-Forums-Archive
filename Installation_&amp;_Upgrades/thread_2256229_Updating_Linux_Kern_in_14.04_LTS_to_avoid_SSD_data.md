---
title: "Updating Linux Kern in 14.04 LTS to avoid SSD data corruption - breaks Nvidia CUDA"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by chris327 on 2014-12-10
Currently Im running a bunch of systems using crucial m500 SSD's with Ubuntu 14.04 LTS

It seems that there is a problem that is causing a lot of data corruption on our drives related to the firmware on the drives and I need to upgrade the kernel to one of the following versions outline in this thread:

[http://forum.crucial.com/t5/Crucial-SSDs/M500-M5x0-QUEUED-TRIM-data-corruption-alert-mostly-for-Linux/td-p/151028](http://forum.crucial.com/t5/Crucial-SSDs/M500-M5x0-QUEUED-TRIM-data-corruption-alert-mostly-for-Linux/td-p/151028)

I am running a Nvidia Titan Black GPU - the drivers (334 found in the supported Ubuntu additional drivers section) work great with the stock kernel but seem to break no matter what kernel I upgrade to

So far I have tried several variants of 3.13.11 and also 3.16

I have tried reinstalling the Nvidia drivers through the additionals drivers dialogue in the system settings but still get the same errors. With the 3.16 kernel I cant even get past the login screen, whereas all of the 3.13 kernels seem to work fine but with no GPU acceleration or CUDA support

Recommendations? At this point a complete reinstall is not out of the question and Im willing to use any kernel that will play well with both our SSD's and Nvidia CUDA

---

### Post by Ferhad_Fidan on 2014-12-15
Installing nvidia-modprobe helped me with some Nvidia problems.

---

