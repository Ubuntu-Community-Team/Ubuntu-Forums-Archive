---
title: "Blank screen after installation, ubuntu dosent load."
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by shanksd on 2007-04-27
I just installed Ubuntu 7.0.4 on my pavillion dv6000 with NVIDIA 6150 go. The installation went smooth, but now when I try to log onto Ubuntu the screen goes black after the "Ubuntu" loading screen...

does anyone know how to correct this? I installed Ubuntu on my desktop with no problems, but the notebook is not going so smooth:(

---

### Post by zvacet on 2007-04-28
```
 sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv** and after that go for drivers

---

### Post by shanksd on 2007-04-28
I cant really type anything or see anyting but black...How might I install the drivers if the screen is blank and I see nothing?

---

### Post by shanksd on 2007-04-28
Ok, so I reconfigured the xserver and the only thing that changes is now after the Ubuntu loading bar there is a blinking curser instead of pure black..

---

