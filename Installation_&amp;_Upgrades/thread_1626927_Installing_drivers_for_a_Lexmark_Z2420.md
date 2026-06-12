---
title: "Installing drivers for a Lexmark Z2420?"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by Hefner22 on 2010-11-20
I downloaded the driver for the exact printer from Lexmark's website.  I then extract the file.  I double click the file and select run in terminal and everything seems to be working like it is supposed to.  But then it asks for my administrative password and every time I enter it, I get a message saying it is incorrect.  But this very same password works for every other program I download?  What would be causing this and how do I fix it? thanks for the help!

---

### Post by wbar2 on 2010-11-21
This is because it is asking for the system's root password, which by default in Ubuntu does not exist. 
Try running the script with sudo in the terminal:

```
sudo sh NAMEOFSCRIPT.sh
```

---

### Post by swajime on 2010-12-24
Is it possible to install the driver on an AMD64?

john@desktop:~$ sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh 
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
TRACKING IDENT = 170209
cpu speed = 1200 MHz
ram size = 3960.41796875 MB
hd avail = 2445 MB
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

---

