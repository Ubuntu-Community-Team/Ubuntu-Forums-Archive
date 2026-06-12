---
title: "An ISO for the dell XPS  M1330, where?"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Carlos Araujo on 2008-01-23
No "just install,no just works"

---

### Post by kellemes on 2008-01-23
> **Carlos Araujo said:**
> No "just install,no just works"

What do you want exactly?
You're not very clear..

---

### Post by Carlos Araujo on 2008-01-23
NO WORKs

Desktop Effects (compiz fusion)
Web cam
Dell Multimedia keys
Screen resolution: Only 1280X720

---

### Post by Philio on 2008-01-23
It does 'just work', but it may depend on your hardware, for example Intel wireless works out of the box but I read somewhere that the Dell Broadcom based cards require additional drivers/setup.

Read this for more info: [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

---

### Post by Philio on 2008-01-23
> **Carlos Araujo said:**
> NO WORKs

Desktop Effects (compiz fusion)
Web cam
Dell Multimedia keys
Screen resolution: Only 1280X720

If you mean the above are not working:

Compiz: Install NVIDIA driver (Applications -> Add/Remove), search for 'nvidia' and select new driver, restart X, then enable Compiz effects.

Webcam: You need V4L2 driver and compatible software.

Multimedia keys: Should work

Screen resolution: System -> Prefs -> Screen Resolution

---

### Post by forestcomber on 2008-01-30
Voilà !

[http://linux.dell.com/files/ubuntu/iso-images/](http://linux.dell.com/files/ubuntu/iso-images/)

---

### Post by szandor on 2008-02-28
> **forestcomber said:**
> Voilà !

[http://linux.dell.com/files/ubuntu/iso-images/](http://linux.dell.com/files/ubuntu/iso-images/)

awesome. thanks. don't know why i couldn't find this. my googling skills suck at 5am.

---

