---
title: "force lower screen resolution ubuntu server i915 KMS on HDMI"
date: 2016-04-07
forum: Installation &amp; Upgrades
---

### Post by alex351 on 2016-04-07
Hi all,

i am running an ubuntu server (16.04 dev) and I am accessing the server via VNC or ssh. In order for VNC to work with the KMS i915 driver I plugged a HDMI dummy plug into the DVI port (with a DVI-HDMI adapter). my issue is that the resolution is always set at 1920x1080px - which is way too large for accessing via VNC on a 1024x768 remote laptop. I would be thankful for a hint on how to change the resolution. I managed to change it for the grub menu but not for what comes afterwards...

thanks
alex

P.s.: its an intel integrated graphics chipset on a xeon 1225v3

---

### Post by roler2 on 2016-04-08
The current kernel that is part of 16.04 does not appear to support the i915 driver. You have to utilize 14.04 and the default kernel, not any of the upgraded kernels that are included with HWE. I was hoping they would fix this however it appears not. I have to stick with 14.04 and the default kernel and then get a computer that does not include the i915 driver.

---

### Post by alex351 on 2016-04-08
Thanks for the info.i hope this gets fixed for the final release. In any case - how would I set the resolution if it would be working?

---

### Post by roler2 on 2016-04-09
It won't be fixed. The i915 driver has been discontinued in terms of kernel support. It should be fixed, but it won't. I utilize 14.04 so I don't know how to fix the resolution on 16.04. It is automatic for me so I don't have to fix the resolution. Lubuntu will have to change the aspect that their OS is good for older computers. Not any more. That is, unless a fix can be applied to include the i915 support via the updated kernel. Many P4's, especially Dell, have the i915 as the default. Lubuntu, Ubuntu and all the others will be rendered useless with these respective P4's without an appropriate fix.

You are probably utilizing a VGA driver since the kernel support for the i915 has been discontinued. If so, there is no way to adjust the resolution. It is not loading the correct driver, just a generic one similar to the one you would find on Windows in Safe Mode.

---

