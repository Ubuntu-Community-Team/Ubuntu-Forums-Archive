---
title: "Can't boot Kubuntu 8.10 beta"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 67GTA on 2008-10-19
I have a HP dv6815 laptop with Nvidia 7150 GPU that is not supported by the nv driver. The Kubuntu 8.10 beta live CD won't boot because it is trying to use the nv driver even when I choose safe graphics mode and xforcevesa. How can I get around this? Xorg.conf is no longer populated, so how do I force vesa at boot? I'm wondering if this needs to be reported so the devs can keep xorg from using nv for this card? The last few lines from /var/log/Xorg.0.log using safe mode...

```
(II) Primary device is: PCI 00@00:12:0
(WW) NV: Ignoring unsupported device 0x10de0531 (GeForce 7150M)
(EE) No devices detected

Fatal server error: no screens found
```

---

### Post by 67GTA on 2008-10-19
Someone is already working on it: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/261977 ]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/261977")I didn't see this report the first time I searched launchpad. I guess I'll have to wait and try the RC:)

---

