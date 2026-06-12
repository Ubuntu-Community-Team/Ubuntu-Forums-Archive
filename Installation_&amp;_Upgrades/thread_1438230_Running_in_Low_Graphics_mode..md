---
title: "Running in Low Graphics mode."
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by keithclark on 2010-03-24
I am getting the following upon booting up after upgrading from 9.10 to 10.04 Beta:

Ubuntu is running in low-graphics mode.
The following encountered.  You may need to update your configuration to solve this

(EE) intel(0):[drm] failed to set drm interface version
(EE) intel(0):Failed to become DRM master
(EE) intel(0):failed to get resources:Bad file descriptor
(EE) intel(0:Kernel modesetting setup failed
(EE) Screen(s) found, but none have a usable configuration.

I then press the OK button (no other option given).

Then I'm presented a menu with the following options:

(x) Run Ubuntu in low-graphics mode for just one session
( ) Reconfigure graphics
( ) Troubleshoot the error
( ) Exit to console login
( ) Restart X

Cancel and OK buttons.  I choose OK and the system seems to boot ok.

I'm not sure what is wrong or how to go about solving this one.

Keith

---

### Post by lemming465 on 2010-03-28
The first thing I'd try is package updates and an X reconfiguration, e.g.```
sudo -i
aptitude update
aptitude full-upgrade
dpkg-reconfigure xserver-xorg
```

---

### Post by mklinux on 2010-06-20
> **lemming465 said:**
> The first thing I'd try is package updates and an X reconfiguration, e.g.```
sudo -i
aptitude update
aptitude full-upgrade
dpkg-reconfigure xserver-xorg
```

I'm getting the same errors as KeithClark up above:

(EE) intel(0):[drm] failed to set drm interface version
(EE) intel(0):Failed to become DRM master
(EE) intel(0):failed to get resources:Bad file descriptor
(EE) intel(0:Kernel modesetting setup failed
(EE) Screen(s) found, but none have a usable configuration.

I tried running the xorg and aptitude update/reconfigure in command, and although the code ran, it didn't solve the problem - I still get the same errors.

Any solutions?

---

### Post by davidmohammed on 2010-06-20
I would try renaming the file /etc/X11/xorg.conf to something else.  Strictly speaking, you dont need an xorg.conf unless you've got non-free proprietary drivers installed.

---

