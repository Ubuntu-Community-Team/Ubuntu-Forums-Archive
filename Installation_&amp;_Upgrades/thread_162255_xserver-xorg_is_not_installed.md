---
title: "xserver-xorg is not installed"
date: 2006-04-18
forum: Installation &amp; Upgrades
---

### Post by ofer_w on 2006-04-18
hi

after installing ubuntu the graphic mode is not loading 
I found on this forum to write 

sudo dpkg-reconfigure xserver-xorg 

but when I write it I get few lines and the last line 
Package 'xserver-xorg' is not installed and no info is available

what should I do?

thanks

---

### Post by oscar on 2006-04-18
Try:
```
sudo apt-get install xserver-xorg
```
This will install it if it is not already installed.
It is possible that you accidentally did the server install which has no desktop/gui. If this is the case try a:
```
sudo apt-get install ubuntu-desktop
```
to install the desktop, it should have all of the right dependencies

---

### Post by ofer_w on 2006-04-18
[QUOTE=oscar]Try:
```
sudo apt-get install xserver-xorg
```
This will install it if it is not already installed.
It is possible that you accidentally did the server install which has no desktop/gui. If this is the case try a:
```
sudo apt-get install ubuntu-desktop
```
to install the desktop, it should have all of the right dependencies[/QUOTE]

thanks for your fast replay

I wrote what you told me and this is what I get

sudo: unable to lookup mysystem via gethostbyname()
postdrop: warning: unable to look up public/pickup : No such file or directory

---

what to do now?
is it possible to install from the disk?

---

### Post by ofer_w on 2006-04-18
[QUOTE=oscar]Try:
```
sudo apt-get install xserver-xorg
```
This will install it if it is not already installed.
It is possible that you accidentally did the server install which has no desktop/gui. If this is the case try a:
```
sudo apt-get install ubuntu-desktop
```
to install the desktop, it should have all of the right dependencies[/QUOTE]

but when I did 
```
sudo apt-get install ubuntu-desktop
```
it did installation of files and the last few lines:
Errors were encountered while processing:
  /var/cache/apt/archives/ttf-baekmuk_2.1-3_all.deb
E: Sub-process /user/bin/dpkg/ returned an error code (1)

what to do?
what this error means?

thanks

---

