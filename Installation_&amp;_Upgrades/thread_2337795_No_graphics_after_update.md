---
title: "No graphics after update"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by rob169 on 2016-09-21
I have just upgraded my Lenovo T530 laptop (Intel HD 4000 graphics) from 14.04 to 16.04. 

I can open text windows (Ctrl+Alt+F1 etc) but despite trying lots of things, can't get any graphics. 

System worked perfectly with 14.04, and can also dual boot to Windows 7, which still works OK.

I have tried reinstalling the drivers:
```
sudo apt-get install --reinstall xserver-xorg-video-intel xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
This made no difference. I have also tried things to do with the resolution to no effect (though that was rather random, I wasn't very clear what I was doing).

I get the following error message during the boot process:
```
[FAILED] Failed to start Load Kernel Modules.
See 'systemctl status systemd-modules-load.services'
```
I can't see anything in systemctl to explain the problem though I don't know what I'm looking for.

I've looked through a lot of log files and not found much.   Xorg.0.log includes the lines (truncated a bit to save typing)
```
AIGLX error: dlopen of .../dri/1965_dri.so failed (.../dri/1965_dri.so: undefined symbol: _glapi_tls_Dispatch)
AIGLX: reverting to software rendering
AIGLX error: dlopen of .../dri/swrast_dri.so failed (.../dri/swrast_dri.so: undefined symbol: _glapi_tls_Dispatch)
GLX: could not load software renderer
GLX: no usable GL providers found for screen 0
   
```
Obviously something isn't loading, but I'm not sure what or how to fix it. Any help greatly appreciated.

---

