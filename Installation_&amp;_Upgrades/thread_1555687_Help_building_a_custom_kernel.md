---
title: "Help building a custom kernel"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by banz on 2010-08-18
Hi all,
 
I need to build a custom kernel for one of my app. This is the instructions they have posted but it is for fedora and my OS is ubuntu 10.04. 
 
[http://www.fogproject.org/wiki/index.php?title=Building_a_Custom_Kernel](http://www.fogproject.org/wiki/index.php?title=Building_a_Custom_Kernel)
 
This is for a pxe server which I need to add additional network drivers onto it so it can pxe boot. I've googled a bit and all the guides is on how to build a kernel for the OS itself. Could someone kindly shed some light on how I can do this? I've asked for help over there but the forums seems a bit quiet.
 
I tried following it without installing yum and I ran 'make xconfig' but I get the following error message,
 
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'. Stop.
make: *** [xconfig] Error 2
 
 
Thanks!

---

