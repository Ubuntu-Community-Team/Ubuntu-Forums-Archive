---
title: "Gutsy (7.10) installation problem on Dell PowerEdge SC420"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by hnipen on 2007-11-22
Hello

I'm trying to install 7.10 desktop on a Dell PowerEdge SC420. The setup fails to autodetect the graphics driver, and the actual driver (Integrated graphics card: Intel E7221) is not listed in the configuration.

If I'm trying to select any kind of generic VGA adapter, the system stops responding, or
The setup fails after multiple shutdowns of the display server

Any suggestions, anyone?

Regards

HN

---

### Post by Ub1476 on 2007-11-22
Maybe this will help?

[http://www.intellinuxgraphics.org/documentation.html](http://www.intellinuxgraphics.org/documentation.html)

---

### Post by hnipen on 2007-11-26
Tough one this

1. I have installed a graphics card from a vey oldie, where I've been getting Ubuntu 7.10 up-&-running. However, it looks like it's not possible to disable the integrated controller on the SC420. This messes up the display server and for some reason makes it impossible to save the configuration. The result is that I have to configure the graphics controller every time I boot the system =:-0

2. Tried 1. above and with updates from Intel, with no luck....

3. Tried all possible Intel drivers, including Intel Generic Driver, no luck

Geez Dell, are you all in the hands of Bill Gates.......

-HN

---

