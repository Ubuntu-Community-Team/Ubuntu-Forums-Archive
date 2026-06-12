---
title: "usb boot, some programs on HD?"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by kardo2 on 2014-04-24
Hi I installed Ununtu to a 4GB flash drive but it really doesn't seem to have enough space. Is it possible to install some programs on internal HD but still keep the boot from usb? The HD is quite old and slow so I'd like to keep from using it as much as possible but could I install some less frequently used programs on it?

---

### Post by sudodus on 2014-04-24
Welcome to the Ubuntu Forums :-)

It seems you have an old computer. If it is so, I suggest that you download and install the flavour ***Lubuntu***, which is smaller (small enough to be installed in a 4GB flash drive). Furthermore, the desktop environment is much lighter than standard Ubuntu, so it runs much faster and smoother.

See this link for more details [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by kardo2 on 2014-04-25
I tried this:
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
but i run out of space after installing libreoffice.

---

### Post by sudodus on 2014-04-25
4 GB is very tight, and will not be enough when you start installing big software packages. It might help if you 'keep the house clean' with the following commands

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

after update and upgrade.

If you want a system with a 'full set' of useful programs, you need at least 8 GB. I would recommend a fast 16 GB pendrive. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

> **Notes about size**

 1  GB is enough for a live USB flash drive made from a 'CD size' iso file.  But unless you already have a 1 GB drive, you are recommended to get  one with at least 2 GB, hence the general recommendation above. 

2 GB is enough for 'CD size' iso files as well as many but not all 'DVD size' iso files. 


If  you want a persistent live system with a decent size casper-rw storage,  you need at least 4 GB (2 GB is possible, but might soon run out of  space). 


If  you want an installed system you need at least 8 GB (4 GB is possible  with Lubuntu, but might soon run out of space). In the beginning of  2014, it seems that there are no really fast pendrives below 16 GB. If  you want a fast system, install it into a pendrive that performs well in  a test, even if it is 'bigger than necessary'. 

and this [link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

