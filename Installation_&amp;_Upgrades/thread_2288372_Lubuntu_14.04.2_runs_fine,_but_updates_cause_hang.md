---
title: "Lubuntu 14.04.2 runs fine, but updates cause hang"
date: 2015-07-26
forum: Installation &amp; Upgrades
---

### Post by destro2k2 on 2015-07-26
Freshly installed Lubuntu 14.04.02 today. This is the third time I've installed. Initially it works perfectly, then I get all updates, then the system hangs at the Lubuntu screen during startup/reboot. After about 15 minutes the Lubuntu screen disappears but the system continues to hang (or progress inperceivably slow) making the system completely unusable. Can anyone help me? Also, the very same thing happens with Xubuntu.

Specs:
P4 1.6GHz proc
1GB mem
40GB hdd
ATI Rage 128 Ultra 32MB AGP VGA Video Card

---

### Post by sudodus on 2015-07-27
It is an old computer. I suspect that you have problems with a hardware driver, probably the driver for your ATI graphics card. An alternative might be to try ***Lubuntu or Xubuntu 14.04.01 LTS*** instead (the previous point release). It has the trusty kernel, while 14.04.2 has the utopic kernel. If 14.04.01 works after

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and reboot, you should avoid upgrading the hardware enablement stack, and you should avoid upgrading to a newer version as long as Lubuntu and Xubuntu trusty are supported (until April 2017).

If you still have problems, I suggest that you try a light-weight community re-spin based on Ubuntu 12.04 LTS, for example ***LXLE, Bento, Bodhi***.

---

### Post by RobGoss on 2015-07-27
I would have to agree your machine is very old and can't handle the OS, you need to try a lighter version of Ubuntu

---

### Post by roler2 on 2015-07-29
[SIZE=3]I am not sure if this will help you as I am not an expert at all. However I believe the 14.04.2 ISO contains the HWE upgrade. I posted about the issues I experienced with the HWE upgrade: "Does manually installing HWE depend on your hardware and/or software [COLOR=#000000][SIZE=3]configuration?" My computer is as old as yours. 

What I want to suggest is downloading the regular Lubuntu 14.04 ISO which contains the default 3.13 kernel. You can update the 3.13 kernel. However don't update to the 3.16 Utopic or 3.19 Vivid kernel. Your computer might be hanging on updates because of an issue with the upgraded kernel and/or X-Org Server, possibly with the video driver. Stick with Lubuntu. I tried Kubuntu and it didn't work very well at all.[/SIZE]




[/COLOR][/SIZE]

---

