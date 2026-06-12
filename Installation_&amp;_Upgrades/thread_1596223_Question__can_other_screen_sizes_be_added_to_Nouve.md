---
title: "Question:  can other screen sizes be added to Nouveau"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by website.reader3 on 2010-10-14
It's been a long long day.  I had to install Ubuntu 10.10 5 times before the boot problem was fixed, but only now to find that the Nvidia GE Force 3 Ti200 video card is NOT supported by the current Nvidia drivers and the legacy Nvidia 96 video drivers has a known bug which may never get fixed.

Currently I am running the 1024 x 768 screen size under Nouveau, but how can I change this to 1920x1080 ?  Will creating an xorg.conf file work?

I did have the GE Force 3 supporting the new 1920x1080p monitors under VGA mode and the screen looked fantastic in the past.

Is the [Ubuntu-x-swat] [Bug 616394] [NEW] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData going to be fixed soon?

I really would like to advance to the higher resolution mode, if possible.

---

### Post by website.reader3 on 2010-10-14
Found the answer, it is by letting the nvidia xconfig create the xorg.conf file, then removing the nvidia driver and substituting the nv driver.

Screen came up 1920x1080 vga and looks great!

---

