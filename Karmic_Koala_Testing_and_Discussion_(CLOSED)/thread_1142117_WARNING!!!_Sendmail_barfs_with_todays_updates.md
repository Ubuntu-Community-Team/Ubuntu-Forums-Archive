---
title: "WARNING!!! Sendmail barfs with todays updates"
date: 2009-04-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-04-28
Just updated with the newest stuff as of 6:20 Pacific---Got a couple of updates & rebooted to check out the new 2.6.30 kernel.  Comes in text-only (no problem)---but it was stopping at starting sendmail....so I booted again with the .28 kernel & it too stopped at sendmail.

I went into one of my alternate systems and chrooted into Karmic...did a aptitude remove sendmail & cleaned all of sendmail & its depends out...then rebooted with the .30 kernel...all fine after that....

Not quite sure what barfed sendmail, but I recommend everyone remove it for at least a couple of days.......

---

### Post by ronacc on 2009-04-28
thanks for the heads up.

---

### Post by DougieFresh4U on 2009-04-28
> **autocrosser said:**
> 

Not quite sure what barfed sendmail, but I recommend everyone remove it for at least a couple of days.......

Here's what it wants to update, don't know if this helps, (abort for now)
```
The following NEW packages will be installed:
  libbind9-50{a} libdns50{a} libisc50{a} libisccc50{a} libisccfg50{a} liblwres50{a} 
The following packages will be REMOVED:
  libpulse-mainloop-glib0{u} 
The following packages will be upgraded:
  bind9-host ca-certificates cli-common cpp cpp-4.3 dnsutils doc-base dosfstools dpkg eject ethtool gcc gcc-4.3 gcc-4.3-base 
  gimp-help-common gimp-help-en gnome-terminal gnome-terminal-data gsfonts gzip iproute iso-codes less libaa1 libarchive1 libattr1 
  libbeagle1 libcairo-perl libcairomm-1.0-1 libcap2 libdaemon0 libdbus-glib-1-2 libexempi3 libfreetype6 libgnutls26 libgtkmm-2.4-1c2a 
  libgtksourceview2.0-0 libgtksourceview2.0-common libijs-0.35 libilmbase6 libkeyutils1 liblapack3gf libsoup-gnome2.4-1 libsoup2.4-1 
  linux-libc-dev mawk python-beagle screen-profiles ubuntu-desktop ubuntu-minimal ubuntu-standard 

```

---

