---
title: "Fresh Ubuntu 10.10 install radeon hd driver problems?"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by Boddie on 2010-12-25
**Hello there!**
     I am new to Ubuntu for the most part, but have done a lot of research on this OS. I just freshly installed version 10.10 32 bit, and the first thing I did was follow[ this]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Unsupported_Hardware_Watermark") tutorial on installing the drivers for my HIS Radeon HD 6850. I really want to get this drivers working so I can use the 3D effects on this OS. 

**When I type fglrxinfo I receive:**

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

**When I type aticonfig I get:**

aticonfig: No supported adapters detected

The proprietary driver was never installed so I know that driver is not interfering. Originally the aticonfig was not found at all but with a little troubleshooting from the link above It seems to work, but obviously not recognize the card. The card works great on my windows 7 setup. If I can't get this working I may just remove Ubuntu all together, but any help would be amazing!

---

### Post by tcchris on 2011-01-09
I have a 5550 and the same problem. I am using the radeon driver now but it is a bit slow

---

