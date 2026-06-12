---
title: "./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: c"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by rippon on 2005-06-23
When I try to install firefox, it tells me this; 
  ```
./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
``` 
So Im gusseing that I need this: libgtk-x11-2.0.so.0   ? Where would I be able to find this (if I need it)
Any help appreciated
-Dan Rippon

---

### Post by IchBin on 2005-06-23
[QUOTE=rippon]When I try to install firefox, it tells me this; 
  ```
./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
``` 
So Im gusseing that I need this: libgtk-x11-2.0.so.0   ? Where would I be able to find this (if I need it)
Any help appreciated
-Dan Rippon[/QUOTE]
 Firefox actually has quite a few deps that you'll need. You'll make it a lot easier by installing Ubuntu's package via 'sudo apt-get install mozilla-firefox'

---

### Post by rippon on 2005-06-24
Thank you

---

