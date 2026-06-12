---
title: "Jre depends on Bin and Bin depends on Jre??"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by pawanh on 2009-12-29
:confused:

I was trying to install Sun-Java-Jre on my Karmic, on which I don't have a direct internet connection. The problem is that the Sun-Java-Jre package depends on Sun-Java-Bin package. But when I tried to install it, it says ke Sun-Java-Bin depends on the Jre package??! A dependency depends on the parent package itself? How can I install Jre on my PC? 

(no direct internet, so apt-get suggestions are futile)

---

### Post by taurus on 2009-12-29
Either download all the dependencies and install everything with

```
sudo dpkg -i *.deb
```
or download the .bin file from Sun and install it by hand.

---

