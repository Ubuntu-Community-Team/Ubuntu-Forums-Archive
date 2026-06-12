---
title: "wubi trying to download the AMD64.iso when I have the i386!"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by aNDoz on 2010-10-17
I got the xubuntu-10.04-desktop-i386.iso file in a folder with WUBI but it still keeps trying to downlaod the amd64 version. how can I stop this?

---

### Post by howefield on 2010-10-17
Try these links...

[https://wiki.ubuntu.com/WubiGuide#Why](https://wiki.ubuntu.com/WubiGuide#Why) is the AMD64 version of Ubuntu getting downloaded and installed?

[https://wiki.ubuntu.com/WubiGuide#Can](https://wiki.ubuntu.com/WubiGuide#Can) I force Wubi to download and install a 32 bit version of Ubuntu?

---

### Post by aNDoz on 2010-10-17
> Yes: either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.

[COLOR="Red"]I always "download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe"
but how do I "start Wubi with the "--32bit" argument" ?[/COLOR]

but it's still downloading the amd64.

just noticed wubi wants the
```
xubuntu-10.04.01-desktop-i386.iso
```
and I got:
```
xubuntu-10.04-desktop-i386.iso
```
(even though I downloaded it JUST now.

I'll copy, paste, change the name :D
brb

---

### Post by aNDoz on 2010-10-17
changing the name doesn't work.
how do I add "the "--32bit" argument"?

---

### Post by bcbc on 2010-10-17
The wubi you have is at release 10.04.1. I don't think there's even a 10.04.1 version of xubuntu, but wubi.exe doesn't care - it's release specific. 

You need the 10.04 version of wubi.exe or it won't work, no matter what you do. wubi-r189.exe from [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/) is for release 10.04 (or look for it on the net, or mount and pull wubi.exe off the xubuntu iso you have)

---

### Post by aNDoz on 2010-10-17
There is a wubi-r190.exe there as well.
should I download that one or does it have to be the r189?
--------------------------------------------------------------
edit:
I downloaded the r189, (sorry for doubting your knowledge ;) )
REBOOT time :D

---

### Post by bcbc on 2010-10-17
> **aNDoz said:**
> There is a wubi-r190.exe there as well.
should I download that one or does it have to be the r189?
--------------------------------------------------------------
edit:
I downloaded the r189, (sorry for doubting your knowledge ;) )
REBOOT time :D

You're absolutely right to doubt everything. I do ;)

---

