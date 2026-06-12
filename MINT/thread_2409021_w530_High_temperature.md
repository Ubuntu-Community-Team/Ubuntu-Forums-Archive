---
title: "w530 High temperature"
date: 2018-12-26
forum: MINT
---

### Post by ginar2 on 2018-12-26
Hi,
I've just switch to Linux Mint 19.1 Cinnamon form Windows.
My hardware is Lenovo thinkpad w520 with two externals monitors connected to DVI via dock station.
What  strange compared to windows is high fun speed. Its enought to play youtube video and fun goes to high speed. I can see that core's temperature is higher compared to windows even in idle state.
I don't see problem when all external moniters plug-off so I suspect graphic chip cause the problem.
```
ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000FFCsv000017AAsd000021F5bc03sc00i00
vendor   : NVIDIA Corporation
model    : GK107GLM [Quadro K1000M][B]
driver   : nvidia-driver-390 - distro non-free recommended
[/B]driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
```

The bolded one driver is which currently in usage.
Not sure what can I do with it. Windows 7 works with exactly the same hardware without any problem.

---

### Post by QIII on 2018-12-26
Moved to ***MINT*** for a more appropriate fit.

---

