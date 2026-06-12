---
title: "need help, i'm new with linux..."
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Tigrius on 2010-01-23
why i can't finish instalation? it shows this message...

In file included from /usr/include/fcntl.h:217,
                 from ../gnulib-lib/fcntl.h:27,
                 from write-catalog.c:25:
In function 'open',
    inlined from 'msgdomain_list_print' at write-catalog.c:223:
/usr/include/bits/fcntl2.h:51: error: call to '__open_missing_mode' declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[3]: *** [write-catalog.lo] Error 1
make[3]: Leaving directory `/home/tigrius/Desktop/gettext-0.17/gettext-tools/src'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/tigrius/Desktop/gettext-0.17/gettext-tools/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tigrius/Desktop/gettext-0.17/gettext-tools'
make: *** [install-recursive] Error 1

---

### Post by mionescu on 2010-01-23
Instalation of what? The OS (which version?), a specific program? Can you describe the steps you did?

---

### Post by Tigrius on 2010-01-23
im using ubuntu 9.10 tried to install gettext for glib i made ./configure and then sudo make install

---

### Post by NIT006.5 on 2010-01-23
What are you trying to install and how are you trying to do it?

---

### Post by NIT006.5 on 2010-01-23
Is there a specific reason you're compiling from source? Packages should be available in the repositories.

```
sudo apt-get install gettext
```

---

### Post by Tigrius on 2010-01-23
at all i need to install usb_modeswitch or something else because i have huawei usb modem and ubuntu shows it like cd drive, so i dont know what to do... and i have wista and ubuntu in same pc and i want to get rid of wista but first i have to get internet connection at ubuntu.

---

### Post by mionescu on 2010-01-23
Why don't you install the gettext package using Synaptic (or the software center)?

---

### Post by Tigrius on 2010-01-23
because i dont have internet connection on ubuntu.

---

### Post by nothingspecial on 2010-01-23
[[COLOR="Magenta"]Here it is[/COLOR]]("http://packages.ubuntu.com/karmic/gettext")

Download it in wista and copy it across. Then click on it.

Check in synaptic that you have all the other packages with red dots infront of them and if you don`t get them too and so on.

---

### Post by NIT006.5 on 2010-01-23
> **Tigrius said:**
> because i dont have internet connection on ubuntu.

Valid point! Excuse my stupidity. Sorry, I can't help with those errors, but you could try downloaded the deb packages (along with any dependencies) from Windows, and then using:

```
sudo dpkg -i
```

to install them on Ubuntu. You're less likely to get errors that way I think, if you're using the official supported packages. I don't have any other ideas at this point.

---

### Post by Tigrius on 2010-01-23
all packages were installed before.

---

### Post by Tigrius on 2010-01-23
> **NIT006.5 said:**
> Valid point! Excuse my stupidity. Sorry, I can't help with those errors, but you could try downloaded the deb packages (along with any dependencies) from Windows, and then using:

```
sudo dpkg -i
```to install them on Ubuntu. You're less likely to get errors that way I think, if you're using the official supported packages. I don't have any other ideas at this point.

Yes i'm using official packages.

---

### Post by Tigrius on 2010-01-23
solved :) connected via LAN and updated all ubuntu :) now everything works fine thx everyone for helping. 

Regards Tigrius

---

