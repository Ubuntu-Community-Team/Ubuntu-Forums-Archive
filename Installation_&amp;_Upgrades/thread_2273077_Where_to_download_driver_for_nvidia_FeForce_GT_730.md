---
title: "Where to download driver for nvidia FeForce GT 730"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by satimis on 2015-04-10
Hi all,

Just built a new box with following config:-

AMD 8-Core FX-8320
Motherboard  ASUS M5A97 LE R2.0 AMD 970
Graphic card  ASUS GT730-SL-2GD3-BRK GT730 (nvidia GeForce GT 730)
RAM 8G
Display  Philips BrilliAnce 200WP

OS - Ubuntu 14.04 64bit

The graphic card couldn't work properly.  On Displays Settings it shows "Built-in Display".  Please advise where can I download the driver for the graphic card.

Thanks

Regards
satimis

---

### Post by grahammechanical on 2015-04-10
When we install Ubuntu we get an option to also install third party software. If we accept that option and tick the box we also get a third party (proprietary) video driver. In your case it would an Nvidia driver. We will get the latest but stable proprietary driver in the Ubuntu software repositories.

When we are running on a proprietary video driver the Displays utility is ineffective. You should have a Nvidia Xserver settings utility already installed. Search in the Dash for Nvidia.

Also you can open System Settings>Software & Updates>Additional Drivers tab. You need to have an internet connection and allow the utility time to do its work. You will get an option of 5 video drivers to choose from. You may find that you are already using an Nvidia driver. If you are using the open source driver then you can change to an Nvidia driver if you want to. Just select the driver and click Apply, and wait and then re-start.

Regards.

---

### Post by satimis on 2015-04-10
> **grahammechanical said:**
> When we install Ubuntu we get an option to also install third party software. If we accept that option and tick the box we also get a third party (proprietary) video driver. In your case it would an Nvidia driver. We will get the latest but stable proprietary driver in the Ubuntu software repositories.

When we are running on a proprietary video driver the Displays utility is ineffective. You should have a Nvidia Xserver settings utility already installed. Search in the Dash for Nvidia.

Also you can open System Settings>Software & Updates>Additional Drivers tab. You need to have an internet connection and allow the utility time to do its work. You will get an option of 5 video drivers to choose from. You may find that you are already using an Nvidia driver. If you are using the open source driver then you can change to an Nvidia driver if you want to. Just select the driver and click Apply, and wait and then re-start.

Regards.
Hi,

According to your advice performed following steps;

-> Settings>Software & Updates>Additional Drivers (clicking this tab)

Software & Update```

NVIDIA Corporation: Unknown
This device is using an alternative driver.
- Using NVIDIA binary driver-version 331.113 from nvidia-331 (proprietary, tested)
- Using NVIDIA binary driver-version 331.113 from nvidia-331 (proprietary)
- (already check) Using X.Org Xserver - Nouveau display driver from xserver-xorg-video-nouveau (open source)

```

Selected FIRST option
-> [Apply Changes]

Rebooted PC.

Now my problem gone.  The display "Philips BrilliAnce 200WP" detected.

Lot of thanks for your advice and time spent


Edit
===
Remark:
I suppose my problem was caused by forgetting to select "third party software" during installing Ubuntu 14.04

Any further action I have to take ?

Regards
satimis

---

### Post by satimis on 2015-04-12
Hi  grahammechanical,

Just got a new Transcend 1TB SSD and connected it to this box.

Installed Ubuntu 14.04 desktop on it, paying special attention to check "install third party software".  On rebooted it was still found that the display "Philips BrilliAnce 200WP" couldn't be detected.  I have to run the steps described on #3 above.

It is quite strange to me.

Regards
satimis

---

