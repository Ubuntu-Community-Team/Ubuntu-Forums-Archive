---
title: "win 7 and ubuntu 12.04 on 2 drives UEFI"
date: 2013-05-26
forum: Installation &amp; Upgrades
---

### Post by Archimedes007 on 2013-05-26
I have installed Windows 7 on an SSD and want to install Ubuntu 12.04 64-bit on another HDD. Please if someone can give me directions step-by-step and better yet if there's a video for this in this forum will be even better.
I went to Youtube and was not happy at all with what I found. I have an UEFI MoBo and know I can commence with the install process from there. But the rest of the process not 100% certain and do not want to go intuitive on a first try.  I know the drive where I want to install Ubuntu will probably shrink it to accommodate the installation.

In addition will Ubuntu upgrades be simply in the future? Another words let's say Ubuntu 16.10[ hypothetical] will I be able to upgrade from 12.04 to Ubuntu 16.10 effortlessly?

Thank you in advance.

---

### Post by fantab on 2013-05-27
How did you install Windows7 on an SSD? Did you install it in UEFI mode? If you are not sure then post the screenshot of your partitions from Windows. If you already have a Ubuntu install disc then boot with, "Try Ubuntu", from desktop open Terminal (ctrl+alt+T), run the following command and post the output here:

```
sudo parted -l
```

Well to answer you question about upgrades: We don't know what future holds. However, clean upgrade depends on various factors, and depending on those it may or may not be as easy. Ubuntu 12.04 is LTS (Long Term Support=5 years). Ubuntu releases LTS every two years, so the next LTS will be probably 14.04. We can upgrade from LTS to LTS. But not jump from 12.04 to 16.04 without upgrading to 14.04. The Ubuntu versions likes 12.10 or 13.04 are NOT LTS=9 months, so you CAN Upgrade from 12.10 to 13.04 but NOT from 12.10 to 13.10, without upgrading to 13.04 first.

---

