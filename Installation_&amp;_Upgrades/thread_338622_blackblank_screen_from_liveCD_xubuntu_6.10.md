---
title: "black/blank screen from liveCD xubuntu 6.10"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by otchie1 on 2007-01-14
Latest Xubuntu liveCD (6.10) booted fine but flicked to a black screen before the desktop started. I have twin SLi nVidia 7600 and an AMD64 but was using the non-64bit installer.

Used ctrl-alt-bksp ctrl-alt-Fn3 and ESC-ESC-ESC in a chimpanzee fashion until I got text mode.

```
cd /etc/X11/
sudo vi xorg.conf
```

# out DRI in modules, # out PCIbus line in video devices, change 'nv' to 'vesa', # out 3 DRI lines of DRI section.

:qw

```
startx
```

error about X running...

sudu rm -rf /var/tmp/lock-0 (or whatever that error calls the file)

```
startx
```

woot!! slow but good enough to install from.

reboot after install works just fine but is in desperate need of the nvidia driver, so...

get a terminal,

```
cd /etc/X11/
sudo vi xorg.conf
```

change 'vesa' back to 'nv', change PCI 2.0.0 to 7.0.0 and un#

:wq

ctl-alt-bckspc

on reboot it's useable and ready to accept a proper nvidia driver.

---

