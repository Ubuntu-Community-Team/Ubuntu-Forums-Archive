---
title: "ATI Radeon 4550 - issues after upgrade to Lucid"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by kenny99 on 2010-05-28
Hi, I've seen a number of similar posts about issues with ATI drivers after upgrading to Lucid, but none which address the issue i'm having. Initially, after upgrading, the booting process was dying with a black screen at the login splash screen. I managed to boot in low graphics mode then install the open source ATI driver (due to the current bug with the proprietary ATI driver), which allowed me to get back to almost normal graphics, except that graphics performance is now really sluggish. 

Can anyone help point me in the right direction for how to troubleshoot this? Strangely, trying to run glxinfo or glxgears results in the following error:


```
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  1
```5

lspci | grep VGA:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]

```

---

### Post by commandant_gogo on 2010-05-28
Same here

```
~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  20
  Current serial number in output stream:  20
```

```
~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
```

Video use 90% of CPU, impossible to watch a movie fluently.

---

