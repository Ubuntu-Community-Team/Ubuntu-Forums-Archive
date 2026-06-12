---
title: "Xorg and VIA Chrome9 HC IGP"
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by stepan3 on 2015-04-14
Hello. I need your help!

I have thin client WYSE x90 with VIA Chrome9 HC IGP graphic card. I want try to start ubuntu live USB. But i have problems with x manager. It seems it did not recognize my video system.
When it starts i se label "Ubuntu" and progress bar. Then i see a lot of gray stripes and screen starts slowly became black. Could you help me? I am very new in Linux.

Million thanks in advance.

---

### Post by tgalati4 on 2015-04-14
VIA chipsets can be problematic.  What graphics driver are you trying to run?

Try to boot into compatibility mode and see if the VIA openchrome driver is loaded:

> tgalati4@Mint17 ~ $ apt-cache search openchrome
xserver-xorg-video-openchrome - X.Org X server -- VIA display driver
xserver-xorg-video-openchrome-dbg - X.Org X server -- VIA display driver -- debugging symbols
xserver-xorg-video-openchrome-lts-quantal - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-quantal-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-openchrome-lts-raring - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-raring-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-openchrome-lts-saucy - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-saucy-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-openchrome-lts-trusty - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-trusty-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-openchrome-lts-utopic - X.Org X server -- VIA display driver
xserver-xorg-video-openchrome-lts-utopic-dbg - X.Org X server -- VIA display driver -- debugging symbols


No switches to modify with the standard *via* driver.

> tgalati4@Mint17 /lib/modules/3.13.0-24-generic/kernel/drivers/gpu/drm/via $ modinfo via
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/gpu/drm/via/via.ko
license:        GPL and additional rights
description:    VIA Unichrome / Pro
author:         Various
srcversion:     A9CBDDA730E66AB46EAB071
depends:        drm
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512


---

### Post by Vladlenin5000 on 2015-04-14
I don't want to be the bearer of bad news but lately I've been noticing a huge increase in reports about many issues with old VIA chipsets. Apparently they worked acceptably up to 12.04. The problems seemed to have started in newer kernels.

---

### Post by stepan3 on 2015-04-14
I try to run default and xforcevesa. I am very new in Linux.... Just i have this old thin client and decide to try. Slax 6 and Ubuntu 6 i may run live usb. Older versions not.
I try Puppy, DAMN a lot of others. Old Android x86 also may run.

---

