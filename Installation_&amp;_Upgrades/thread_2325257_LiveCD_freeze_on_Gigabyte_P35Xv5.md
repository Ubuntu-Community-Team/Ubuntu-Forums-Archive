---
title: "LiveCD freeze on Gigabyte P35Xv5"
date: 2016-05-20
forum: Installation &amp; Upgrades
---

### Post by UfoXp on 2016-05-20
I get freeze on splash screen while trying to boot 16.4 LiveCD. If I press F10 before freeze I can see load process logs and last lines before freeze say:
[IMG]http://s32.postimg.org/9zua5ov0l/IMG_2373.jpg[/IMG]

I thought about trying various boot options but command line that apears after pressing e on selection screen does not allow me to type in =. It inputs + instead.

[UPDATE]
Now typing in = works. I do not know whether connecting of external keyboard contributed to that... I've tried pci=nomsi and that got rid of PCIe bus error but the rest got stuck as usual :|
The LiveCD boots just fine on my other laptop.

[UPDATE2]
Booting in "legacy" mode causes non-UEFI Ubuntu UI to appear but after proceeding it ends up with same freeze.

[UPDATE3]
Same problem with 15.10...

Any ideas what to do?

---

### Post by UfoXp on 2016-05-26
I finally figured out what was wrong. I've turned on kernel debugging by adding debug parameter to boot options. Afterwards I got pretty clear report of what was getting stuck (sorry for the orientation...):
[IMG]http://s33.postimg.org/qmamdl1tb/IMG_2384.jpg[/IMG]
So the problem was Nouveau driver. Adding nomodeset did take care of disabling it. My install boot command become:
[IMG]http://s33.postimg.org/ji3dopfsf/IMG_2385.jpg[/IMG]
Install worked pretty well and system started afterwards without a hitch (thanks to updates being downloaded during install?). Unfortunately driver still gets stuck during shutdown so everytime I want to close system I have to force quit it... Not nice but I'll live with it for now.

PS
I've tried to install official Nvidia drivers but those get stuck on login :| Or rather X server does?

---

### Post by mario71 on 2016-05-27
If you are not gaming or detecting performance issues with the default open source drivers i would recommend not installing Nvida drivers.

---

