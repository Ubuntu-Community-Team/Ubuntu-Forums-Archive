---
title: "Graphics and Wireless card not detected after install."
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mike_IronFist on 2009-10-17
I installed Karmic 64-bit after deleting 64-bit Jaunty. The Live CD detected my hardware when it was running, and I was able to see that drivers could be installed for it, but after installing and rebooting, my fresh install doesn't detect my hardware at all! Opening Hardware drivers doesn't show any available drivers for my hardware at all!

[[IMG]http://img96.imageshack.us/img96/6452/screenshotix.th.png[/IMG]](http://img96.imageshack.us/i/screenshotix.png/)

**EDIT:** So here's the weird thing... after reinstalling the modaliases package for broadcom drivers, the problem went away. My hardware was detected, and via an ethernet connection, I was able to get my broadcom wireless drivers running. Here's what I did:

1. I opened Synaptic Package Manger. System -> Administration -> Synaptic Package Manager

2. I reinstalled the "Modaliases for the Broadcom 802.11 Linux STA driver". To find it, type the following into the quicksearch bar:
```
bcmwl-modaliases
```
Right click it, and mark it for reinstallation. Click the Apply button.

3. If you're still not getting anything detected after closing Synaptic Package Manager and opening Hardware Drivers (System -> Administration -> Hardware Drivers), plug your laptop into an ethernet cable, plug that cable into a router, and use Synaptic Package Manager to install the "Broadcom 802.11 Linux STA wireless driver source". This can be found by typing the following into the quicksearch bar:
```
bcmwl-kernel-source
```
Right click it, and mark it for installation. Click the Apply button.

4. After doing this and closing Synaptic, then opening Hardware drivers, my hardware was all detected. I restarted my computer, after which point my wireless was working, and I used my spiffy new wireless connection to install the "NVIDIA graphics driver version 185" via Hardware Drivers.

[[IMG]http://img245.imageshack.us/img245/7906/screenshotbu.th.png[/IMG]](http://img245.imageshack.us/i/screenshotbu.png/)

---

