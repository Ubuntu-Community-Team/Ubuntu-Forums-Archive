---
title: "Ubuntu 18.04.1 Dual monitor (Intel + Nvidia GPU) Problem"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by wyzp on 2018-10-21
I was using Mint 19, but after some problems I decided to move to Ubuntu, but I'm facing a really annoying problem since It was working normal in Mint 19.

```
My setup is

Ubuntu 18.04.1
Dual GPU GP107M [GeForce GTX 1050 Ti Mobile] + Intel
Kernel 4.15.0-36-generic (Tested kernel 4.17 and 4.18, same problem)
Nvidia Driver 410.66 (Tested 396 and 390, same problem)
Secure Boot Off (Not sure if its relevant)
```

[ALL INFO (UBUNTU 18 OUTPUT)]("https://pastebin.com/gdXir16U")

So, I clean installed Ubuntu, installed nvidia drive and it seem to work, but well... it partially works. I searched A LOT and it seem to affect some users (most often no solution).

**Main Problem :** My TV/Second monitor is not recognized in the HDMI port.

**Some add info :** If I select *prime-select intel* and reboot, I can't open Nvidia-settings (Nvidia driver is not been load) it didn't happen in Mint 19, I was able to open Nvidia settings using both nvidia or intel in PRIME, I can still change nvidia and intel in terminal *sudo prime-select nvidia/intel*.

By default there's no xorg.conf in /etc/X11. Once I enter *sudo nvidia-xconfig* it generates two files */etc/X11/xorg.conf* and */etc/X11/xorg.conf.nvidia-xconfig-original* (see OUTPUT), BUT after these files are created using *prime-select nvidia* Ubuntu won't pass Login Screen, it freezes after enter password, It boots normal using *prime-select intel*.
**-- EDIT --**

Installed Linux Mint 19 again, clean flash, install nvidia driver and well... It just works normal, no problem at all. I took the same outputs and notice just a briefly difference in *xrandr *that shows eDP-0 and HDMI-0. Anyway, If someone like me really needs a Dual Monitor, the best way for now is to try Mint 19

[MINT 19 OUTPUTS]("https://pastebin.com/dKfA2z4H")

---

