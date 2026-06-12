---
title: "wubi don't run in my windows 7 sp1"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by ehsan957 on 2013-04-08
Hi my masters,
I have windows 7 sp1 64-bit on my PC,
I download ubuntu-12.04.2-desktop-amd64.iso from ubuntu.com and copy wubi in folder of it and run as administrator but after show UAC don't show anything,
What's reason?

---

### Post by bcbc on 2013-04-08
You should check for the log file in the %TEMP% directory. Sometimes Wubi.exe will fail silently over an unknown ISO. Sometimes it's a python compatibility issue. But always check for the log file first: wubi-12.04.2-revxxx.log

Oh and PS due to a bug in Wubi, it will not be able to use the 12.04.2 ISO and instead will download the diskimage, because of a kernel name change on the 12.04.2 AMD64 ISO unfortunately: [https://bugs.launchpad.net/wubi/+bug/1134770](https://bugs.launchpad.net/wubi/+bug/1134770)

---

