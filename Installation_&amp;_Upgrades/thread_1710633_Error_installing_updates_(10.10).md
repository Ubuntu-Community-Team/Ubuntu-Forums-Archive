---
title: "Error installing updates (10.10)"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by yae7 on 2011-03-20
HI

i am trying to install updates from synaptic and lxterminal. but is impossible. 

attach capture

---

### Post by Jared Norris on 2011-03-22
Can you open up your terminal and type in:

```
sudo apt-get update
```

And then type in your password if prompted. If that works fine without any errors then type in:

```
sudo apt-get upgrade
```

If you can please post back if you get any errors that would help troubleshoot this further.

---

### Post by yae7 on 2011-03-26
> **head_victim said:**
> 
```
sudo apt-get upgrade
```

If you can please post back if you get any errors that would help troubleshoot this further.

yes, display this error:

[COLOR="Purple"]dpkg: error en el análisis, en archivo «/var/lib/dpkg/status» línea cercana 9894 paquete «libgp11-0»:
 valor duplicado para el campo `Package'
E: Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR]

---

### Post by Jared Norris on 2011-03-26
I'm not sure I translated it perfectly but I think if you have a look at: [https://answers.launchpad.net/ubuntu/+source/dpkg/+question/40321]("https://answers.launchpad.net/ubuntu/+source/dpkg/+question/40321") it might help you out a bit because I think the person who asked that question has the same error as you. It won't be the exact same package you're having problems with but should give you a good idea how to solve your issue.

Let us know if it's still not working after this.

---

### Post by yae7 on 2011-03-26
same error.

If i open "status" file and search on line 9894, I have this:


> Package: libgp11-0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 200
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: gnome-keyring
Version: 2.92.92.is.2.31.91-0ubuntu4.1
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.24.0)
Description: Glib wrapper library for PKCS#11 - runtime
 GP11 is a wrapper based on GLib implementing the PKCS#11 (Cryptoki)
 interface.
 .
 This package contains the shared libraries needed to run programs
 built against the GP11 library.
: Josselin Mouette <joss@debian.org>

is incorrect?

---

### Post by Jared Norris on 2011-03-26
Well the first thing I would try according to that would be:
```
sudo dpkg --configure -a
```
And then the usual 
```
sudo apt-get update && sudo apt-get upgrade
```

If that didn't work then I would try removing the package cache. This should either be
```
sudo rm /var/cache/apt/pkgcache.bin
```
or something starting with (I'd use tab completion on the following line to get the correct file)
```
sudo rm /var/cache/apt/archives/libgp
```
And then try ```
sudo apt-get update && sudo apt-get upgrade
```

One of those 2 options should fix the error from what is posted in the previous link.

---

### Post by yae7 on 2011-03-26
I have tried.  but continues displaying the same error :(

```
Des:1 http://es.archive.ubuntu.com/ubuntu/ maverick-updates/main libglib2.0-0 i386 2.26.1-0ubuntu1 [1381kB]
Des:2 http://es.archive.ubuntu.com/ubuntu/ maverick-updates/main libglib2.0-data all 2.26.1-0ubuntu1 [976B]
Descargados 1382kB en 4s (277kB/s)
Extrayendo plantillas para los paquetes: 100%
Preconfigurando paquetes ...
[COLOR="Red"]dpkg: error en el análisis, en archivo «/var/lib/dpkg/status» línea cercana 9894 paquete «libgp11-0»:
 valor duplicado para el campo `Package'
E: Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR]
```

---

### Post by yae7 on 2011-03-26
i have found the solution! :D 

simply:

```
cd /var/lib/dpkg
ls status*
sudo mv status status-bad
sudo cp status-old status
```

Here: [http://ubuntuforums.org/archive/index.php/t-1501743.html](http://ubuntuforums.org/archive/index.php/t-1501743.html)

---

### Post by Jared Norris on 2011-03-27
Great news! Sorry I couldn't be more helpful but thanks for posting the fix so that others can benefit.

---

