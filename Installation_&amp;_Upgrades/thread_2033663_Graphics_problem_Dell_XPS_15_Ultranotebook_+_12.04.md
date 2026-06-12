---
title: "Graphics problem: Dell XPS 15 Ultranotebook + 12.04"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by sierra1bravo on 2012-07-26
Dear all
The installation went off well, and most things work fine. I am making separate posts on two things that didn't go so well: Graphics and Suspend/Hibernate/Shutdown.

glxinfo crashes with:

```
name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

lspci | grep VGA returns:
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

Many graphics-intensive applications crash on launch (eg., Google Earth, Stellarium etc) and Unity cannot shift to 3D mode.

Any help is much appreciated.


s1b

---

### Post by dino99 on 2012-07-26
is it with genuine driver or ppa ? maybe you can try both (for example edgers ppa)

---

