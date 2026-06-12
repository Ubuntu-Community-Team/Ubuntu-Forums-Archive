---
title: "[Linux Mint 17.2] latest driver installed, can't enable Nvidia GPU"
date: 2015-08-10
forum: MINT
---

### Post by hawkzy2 on 2015-08-10
Edit: made a new post in the Mint forum [http://ubuntuforums.org/showthread.php?t=2290244](http://ubuntuforums.org/showthread.php?t=2290244)

I installed the xorg-edgers PPA listed in this guide [http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/) and applied the latest driver version (352.30) via the Driver Manager. (I checked the nvidia website for which version to use for my card.) But then when I go to enable the card via the Nvidia X Server Settings, it gives me a blank error popup, and then reverts back to using the (CPU-integrated) Intel GPU after closing it.

I've also spent the past day and a half trying to get this card (GT 740) to work properly on Debian 8.1. I played around with the drivers and Xorg and ended up reinstalling Debian several times in the process, while finding no solution and deciding to switch to Mint for better compatibility. I do, however, like Debian quite a bit more so if anyone happens to have a solution for that problem I can supply some more details about those issues. (Though I am perfectly fine using Mint)

Ideas?

---

### Post by hawkzy2 on 2015-08-10
I installed the xorg-edgers PPA listed in this guide [http://www.binarytides.com/install-n...-ubuntu-14-04/]("http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/")  and applied the latest driver version (352.30) via the Driver Manager.  (I checked the nvidia website for which version to use for my card.) But  then when I go to enable the card via the Nvidia X Server Settings, it  gives me a blank error popup, and then reverts back to using the  (CPU-integrated) Intel GPU after closing it.

I've also spent the past day and a half trying to get this card (GT 740)  to work properly on Debian 8.1. I played around with the drivers and  Xorg and ended up reinstalling Debian several times in the process,  while finding no solution and deciding to switch to Mint for better  compatibility. I do, however, like Debian quite a bit more so if anyone  happens to have a solution for that problem I can supply some more  details about those issues. (Though I am perfectly fine using Mint)

Ideas?

---

### Post by efflandt on 2015-08-12
I have not tried Mint lately. But my laptop with Intel HD 4600 / Nvidia GTX 765M works fine in 64-bit Ubuntu 14.04 just using nvidia-331-updates package from the normal Ubuntu repositories. Newer nvidia graphics might need a newer driver, but that should not be an issue for GT 740 (although, it is not clear if this is GT 740 added to a desktop or GT 740M on a laptop). If it is a desktop maybe you need to do something in BIOS to disable your Intel video.

Maybe one thing to note is that nomodeset is typically needed as a boot parameter when installing Ubuntu on a desktop PC with nvidia graphics. However, I had see a post from someone who said that did NOT work for hybrid (dual) graphics on a laptop. So I did not use nomodeset when installing 14.04 on my laptop (which boots/runs from mSATA SSD card).

---

### Post by PaulW2U on 2015-08-12
Threads merged. Please do not create duplicate threads.

---

### Post by hawkzy2 on 2015-08-12
> **efflandt said:**
> I have not tried Mint lately. But my laptop with Intel HD 4600 / Nvidia GTX 765M works fine in 64-bit Ubuntu 14.04 just using nvidia-331-updates package from the normal Ubuntu repositories. Newer nvidia graphics might need a newer driver, but that should not be an issue for GT 740 (although, it is not clear if this is GT 740 added to a desktop or GT 740M on a laptop). If it is a desktop maybe you need to do something in BIOS to disable your Intel video.

Maybe one thing to note is that nomodeset is typically needed as a boot parameter when installing Ubuntu on a desktop PC with nvidia graphics. However, I had see a post from someone who said that did NOT work for hybrid (dual) graphics on a laptop. So I did not use nomodeset when installing 14.04 on my laptop (which boots/runs from mSATA SSD card).

It's a 740 put into a desktop that already had integrated graphics. I haven't tried setting nomodeset, but I think I tried blacklisting nouveau, which did not work. Something I realized yesterday was that the card wasn't seated properly in the PCI-e slot; however, fixing that has not helped my issues thus far.

I have since installed Debian 8.1 over Mint and am about to re-install Mint in dual-boot so I can try this with two distros at once and see which one fixes easier, since I do like Debian more.

I've also tried Bumblebee on Debian, which has not worked. Running anything with optirun returns:
```
optirun glxgears
[ 1425.799638] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied

[ 1425.799666] [ERROR]Aborting because fallback start is disabled.

```

And the card is detected by the system:
```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 740] (rev a1)

```

> **PaulW2U said:**
> Threads merged. Please do not create duplicate threads.

Thank you. I would have deleted the first one if I could, I didn't realize there was a Mint section until after I posted the first in official Hardware. I will be more aware in the future.

---

