---
title: "Light server install with 64-bit ARM (ARMv8/AArch64) desktop image"
date: 2021-04-11
forum: Installation &amp; Upgrades
---

### Post by lalalalal10 on 2021-04-11
Hi, can someone help me with a tutorial to install ubuntu 21.04 on a headless arm v8 server (with wired eth connection)?
Does the desktop image have a script to start a server install?

---

### Post by ActionParsnip on 2021-04-11
I suggest you use 20.04 for a server. It is supported for 5 years unlike 21.04 which is only supported for 9 months.

If you create a FAT32 part on your SD card then use something like the Pi Imager application, then you can put the server image on the SD card and boot it in your hardware. You can upgrade the configuration files in the "boot" drive (which is Windows read/writable) to set network options as you require.

---

### Post by lalalalal10 on 2021-04-12
Thank you - that worked!

---

