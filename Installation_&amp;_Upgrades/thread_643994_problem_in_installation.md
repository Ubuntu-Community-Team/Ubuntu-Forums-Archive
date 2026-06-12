---
title: "problem in installation"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by nimagh on 2007-12-18
hi,
I am a new user in Linux and Ubuntu too.
I have installed the Ubuntu for my AM2-64 bit, but when it rebooted after unmounting the cd rom. the ubuntu doesnt works and it seems that it cannot configure my ATI x1600 pro(graphic card). I have the driver from ATI website.how can i Install this driver on my system when th ubuntu cannot boot completely.
:confused:

---

### Post by elliotjreed on 2007-12-18
Boot into safe mode, and type:

```
dpkg-reconfigure xserver-xorg
```

... This will allow you to set the driver, you will either want fglrx or radeon (try fglrx first!), if those do not work, just set the driver to VESA (or was it VERSA?) to allow you to boot in graphically!

---

