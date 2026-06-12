---
title: "i915 Intel Video"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by gambothell on 2012-02-11
**Hardware and configuration**
Acer Aspire 5732Z, 3Gb RAM, 250Gb HD, Intel Mobile 4 Series Graphics Controller (rev 09)
Ubuntu 11.04, Gnome: 2.32.1, Kernel: 2.6.39-0-Generic, Xorg: 1.10.1

**Original Problem**
When I did a fresh install of Ubuntu 11.04, I would boot into a blank or black screen both from CD and USB iso. I went to 11.04 from 10.10 which had no problems with my hardware. After much frustration and searching forums, I added "acpi_osi = Linux" after the "quiet splash" in the boot sequence which corrected the problem. 

This change has worked fine until a receint Ubuntu update. I think it was when Kernel 2.6.39-0-Generic was installed. Now when I boot, at first my screen has the correct background color, but then goes blank or black. Ubuntu does finish booting, but I do not see anything! Please note, that if I unplug my power supply and boot off of the battery, Kernel 2.6.39-0 boots up properly. I think that this is a backlight issue for the Intel i915 graphics. After plugging the line power back in, I am still good to go, but really, this is not a good permanent alternative.

This problem led me to want to upgrade to Ubuntu 11.10 and/or Linux Mint 12. With both these distributions, I get the blank or black screen problem booting from a CD or USB iso. The only way I have been able to get either of these to boot properly with my i915 Intel video, is by adding "i915.modeset=0" after the "quiet splash" in the boot up sequence. But now I have an additional issue which is a show stopper for me. The quality of the screen in both 11.10 and mint 12 is very poor. The fonts are fuzzy and the graphics are streched. I hate to be critical, but the screen appearance is not good enough for me to want to go to the current release, which leaves me with the nuisance issue.

I am posting this, because I know this is not just an Acer problem. Everyone who has Intel i915 video is going crazy, just Google it. Does anyone know if a patch is in the works to address these issues for 11.04 and newer releases? I hope this family of laptops with this inexpensive Intel video is not left in the dust!

---

