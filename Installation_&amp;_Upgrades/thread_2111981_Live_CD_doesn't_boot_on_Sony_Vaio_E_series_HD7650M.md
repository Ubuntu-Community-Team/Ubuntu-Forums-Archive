---
title: "Live CD doesn't boot on Sony Vaio E series HD7650M"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by psychok9 on 2013-02-03
Hello all!
I'm fighting with a Sony Vaio E Series SVE1712Z1EB and Ubuntu 12.04.1 or 12.04.2 (daily).
It doesn't start from USB and show a violet/blackscreen before I can see the GUI neither if I remove "quiet splash" and I add "nomodeset" and "noacpi" command on kernel line (Grub).

The kernel on 12.04.2(daily,not final) is the 3.5.xxx version.

Laptop specs:
Intel Intel® Core&#8482; i7-3632QM (HD4000 hardware disabled)
Intel HM76 Express
AMD Radeon&#8482; HD 7650M
17.3" LCD (1920x1080) pixel Full HD

---

### Post by psychok9 on 2013-02-03
I've installed ubuntu 12.04.1 alternate CD amd64, twice (not completely the 1st time, it seems to have a problem with the installation from the USB drive).
2) I'm fighting again vs iwconfig&&co without any result (dhclient can't do the wlan link and don't show any error, only blinking. I've also tried without key/WEP or WPA, totally open).
3) Linked the classic ethernet cable, I've started Ubuntu on recovery mode. I've typed apt-get update && apt-get upgrade and done all the updates... but when it restarts, the GUI screen doesn't show anything. I've also tried the classic "nomodeset". No result.
4) From the terminal recovery mode, I've copied amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run and installed it. I've tried every configurations I can think:
```
aticonfig --initial
aticonfig --initial --resolution=0,1920x1080
aticonfig &#8722;&#8722;initial=dual&#8722;head --resolution=0,1920x1080
```
No results...
Any suggestion?

---

### Post by psychok9 on 2013-08-21
*deleted*

---

