---
title: "x86 emulator?"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by bigseb on 2010-03-30
i found software i want to use but according to the softwares website it is only 32bit. since i am running 9.10 x64 is there an emulator that will allow me to run this software?

---

### Post by bigseb on 2010-03-30
Someone... please?

---

### Post by benmoran on 2010-03-30
You can do a "force install" using dpkg on the command line. It will probably work fine. There are 32-bit compatibility libraries that you probably already have installed, or are easy to install if not. It's too late to go into more detail, but you can find by searching. That, or i'm sure someone else will chime in. 

What program are you trying to install anyway?

---

### Post by bigseb on 2010-03-30
> **benmoran said:**
> What program are you trying to install anyway?

It's called FreeCAD. One of few solid-modellers available for linux.

---

### Post by azagaros on 2010-03-30
You can download the freeCAD and compile it for 64bit. It is an opensource code.

---

### Post by srs5694 on 2010-03-30
There's a good chance that the [Debian package](http://packages.debian.org/sid/amd64/freecad/download) would install and work correctly in Ubuntu. Download it, then use dpkg to install it:

```

dpkg -i freecad_0.9.2646.5-1+b1_amd64.deb

```

If you get error messages, you might need to track down a different binary file. If it installs OK but doesn't work, uninstall it with dpkg:

```

dpkg --purge freecad

```

---

### Post by foxmulder881 on 2010-03-30
There's no reason the aforementioned Debian package wouldn't work on Ubuntu providing all the libs and deps are installed.

---

### Post by Slim Odds on 2010-03-30
Try this: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by bigseb on 2010-03-31
Thanks everyone! you have been a great help.

---

