---
title: "Two Nvidia Cards - different drivers?"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by foomonster on 2011-03-23
Hope someone here can help with this - seem to be going round in circles a bit.

I've got two Nvidia cards in my PC - an NVS300 and an FX5500. Both are listed in lspci, which is a start:

0d:00.0 VGA compatible controller: nVidia Corporation Device 10d8 (rev a2)
11:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

In my hardware drivers, I've got 270 enabled, and the NVS300 is working fine. However, the FX5500 isn't - getting the following in my startup messages:
[    8.351507] NVRM: The NVIDIA GeForce FX 5500 GPU installed in this system is
[    8.351509] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers. Please
[    8.351510] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[    8.351511] NVRM:  information.  The 270.29 NVIDIA driver will ignore
[    8.351512] NVRM:  this GPU.  Continuing probe...

If I switch to the version 173 drivers, the errors about the FX5500 go away, but the NVS300 is then not supported.

Seems to me that I need to have both the 173 and 270 drivers activated to get this working, which is obviously (presumably?) impossible...

Anyone got any bright ideas about what I can do to get both of these cards working together? Eventual aim is to get 3/4 monitor support up and running, but the obvious first step is to get this cards working together at the same time.

Thanks for any help/pointers/etc.,

J

---

### Post by tommcd on 2011-03-24
> **foomonster said:**
> 
Seems to me that I need to have both the 173 and 270 drivers activated to get this working, which is obviously (presumably?) impossible...

As far as I know, it is indeed impossible to use 2 versions of the nvidia driver at the same time. You will likely need to use 2 nvidia cards that are supported by the same driver.

---

### Post by foomonster on 2011-03-24
Thanks for that - saves me trying to muck around with this for hours.

Really frustrating bit is that the nvidia site says the 260 drivers support both cards - tried installing 260 last night, and the installation program said to use the older drivers for the fx5500...this means buying a new card will be a bit of pot luck as to whether or not it is really supported (unless I just go for another nvs300, I guess).

---

