---
title: "Install Ubuntu 12.04.2 inside windows from alternate ISO"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by M Star on 2013-04-26
I've downloaded the alternate ISo for Ubuntu 12.04.2. How may I install that inside my windows7 installation? Where can I find WUBI for that iso image?

---

### Post by bcbc on 2013-04-26
You can't install Wubi from an alternate ISO. For 12.04.2, if you want to install from a 32bit *desktop* ISO, you can save it in the same folder as wubi.exe before running (both available from [http://releases.ubuntu.com/12.04]("http://releases.ubuntu.com/12,04")
This wubi.exe can also install standalone (no ISO).

To install from the 64bit desktop ISO (not alternate), there is a bug which has been patched, but not released so you'll need to use the wubi.exe from here: [http://people.canonical.com/~evand/wubi/precise/wubi-r273-signed.exe](http://people.canonical.com/~evand/wubi/precise/wubi-r273-signed.exe) (it's signed by Canonical). Save that in the same folder as the desktop-amd64 ISO before running.

---

### Post by fantab on 2013-04-26
I don't think you have WUBI on "alternate" ISO. Moreover WUBI is not really a recommended way to dual-boot Ubuntu with Windows, at least not by me.

Instead you can download a 'regular' Ubuntu and burn it on a USB (4+GB) with persistence using 'Unetbootin' and try it until you are ready to install it on a HDD. WUBI is just to "Try Ubuntu" for a longer duration than default Live DVD/USB.

However, you can find WUBI on 'regular' Ubuntu ISO.

---

### Post by hissam on 2013-05-05
> **bcbc said:**
> You can't install Wubi from an alternate ISO. For 12.04.2, if you want to install from a 32bit *desktop* ISO, you can save it in the same folder as wubi.exe before running (both available from [http://releases.ubuntu.com/12.04]("http://releases.ubuntu.com/12,04")
This wubi.exe can also install standalone (no ISO).

To install from the 64bit desktop ISO (not alternate), there is a bug which has been patched, but not released so you'll need to use the wubi.exe from here: [http://people.canonical.com/~evand/wubi/precise/wubi-r273-signed.exe](http://people.canonical.com/~evand/wubi/precise/wubi-r273-signed.exe) (it's signed by Canonical). Save that in the same folder as the desktop-amd64 ISO before running.



:guitar:):P:p;)  THIS WORKED FOR ME, IAM INSTALLING FOR LAPTOP

---

