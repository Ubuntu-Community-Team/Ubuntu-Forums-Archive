---
title: "NW102 Pleaxgear nettwork adapter driver error"
date: 2024-03-12
forum: Installation &amp; Upgrades
---

### Post by cyberrobotic on 2024-03-12
[COLOR=#0C0D0E][FONT=-apple-system]I have bought NW102 PLEXGEAR wifi adapter try to install the driver on my raspberry pi 4. I get following error when trying to run the driver fille install.sh downloaded from homepage.
[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]I get following error message
[/FONT][/COLOR]```
Authentication requested [root] for make driver:
make ARCH=aarch64 CROSS_COMPILE= -C /lib/modules/5.4.0-1104-raspi/build M=/home/torehaav/Desktop/594290_61346-driver---manual/Driver/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-1104-raspi'
Makefile:705: arch/aarch64/Makefile: No such file or directory
make[1]: *** No rule to make target 'arch/aarch64/Makefile'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-1104-raspi'
make: *** [Makefile:1551: modules] Error 2    
##################################################

Compile make driver error: 2

Please check error Mesg

##################################################

```

[FONT=-apple-system]Any suggestion to solve this problem?[/FONT]
[FONT=-apple-system]Have a nice day[/FONT]

---

### Post by TheFu on 2024-03-13
First question, does the driver and wifi support the ARM64 platform?
If you need things to "just work", buy things that are known to "just work" for the specific platform.

If course, use wired ethernet whenever possible. That's the best option.
!
I searched for anything related to plexgear and couldn't find their website!  I'd definitely avoid their hardware. They don't have a website!? Seriously?

---

### Post by cyberrobotic on 2024-03-13
The driver can found be found here
[https://www.kjell.com/no/varemerker/plexgear/nettverk/tradlost-nettverk/tradlose-nettverkskort/plexgear-tradlost-usb-nettverkskort-600-mbs-p61346](https://www.kjell.com/no/varemerker/plexgear/nettverk/tradlost-nettverk/tradlose-nettverkskort/plexgear-tradlost-usb-nettverkskort-600-mbs-p61346)

---

### Post by TheFu on 2024-03-13
Did you try the RTL8811AU driver?  Is that supported on ARM64?

---

### Post by cyberrobotic on 2024-03-14
I am currently trying to install following driver

I have downloaded driver from [https://github.com/morrownr/8821au-20210708](https://github.com/morrownr/8821au-20210708)
but my driver does not show up when I type nmcli device status

---

