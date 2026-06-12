---
title: "How to delete swap partition?"
date: 2015-11-04
forum: Installation &amp; Upgrades
---

### Post by amantripathi4u on 2015-11-04
Hello Community,, 
I was using Kubuntu 15.10 in dual boot configuration with Windows 10. At the time of installation, I allocated approx 50 GB space to "/", and 15 GB space to home. My machine has 8 GB of RAM, hence I didn't allocate any space for swap, also there was no option to select a space for swap in installation wizard (may be because I already have enough RAM). Furthermore because of some glitches and problems in Kubuntu I decided to do a fresh install of Ubuntu 15.10 over Kubuntu. During the installation I selected "Erase Kubuntu 15.10 and install 15.10" (or something similar), instead of "Something else" and doing disk setup myself. And because of that it created a swap partition of 8 GB automatically. Also it auto-included /home in "/" directory and left previous home partition intact. As I said I have adequate amount of RAM hence swap partition is always empty (or less than 5 mb). I want to reclaim that space. 

I want to move my /home partition to the partition which was left, or to the separate partition.

Kindly suggest me ways to resolve both issues.

Thanks in advance.

---

### Post by Cavsfan on 2015-11-05
You could boot with a live cd and resize the swap partition with gparted. Then resize the another partition to absorb that space.

I have a 1MB swap file. With 4GB RAM or more the only reason one would need a huge swap file is to hibernate. I never hibernate but suspend instead.

Unless someone knows how to do away with the swap file altogether, I'd just make it tiny like mine.

I like it because when I had the swap file bigger, the hibernate option would be available but if I tried it, it would just shut down and a reboot would occur if I pressed the power button.

Having a 1MB swap file causes the hibernate option to be grayed out which is nice.

---

### Post by amantripathi4u on 2015-11-06
thanks for your answer CavsFan

---

### Post by Cavsfan on 2015-11-07
> **amantripathi4u said:**
> thanks for your answer CavsFan

You are welcome. So, you got your swap file downsized? Booting with a liveCD is always good for tuning up partition space.

I once had about 6-7 different systems on this box but down to 3 now.

---

