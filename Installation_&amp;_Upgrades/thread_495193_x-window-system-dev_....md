---
title: "x-window-system-dev ..."
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by sisyphos on 2007-07-07
Hello world!

I am about to install a wacom-tablett on my ubuntu-box. In the beginning I tried to install via synaptic. It worked out fine, except for the fact that this driver seems to ignore wacom on the serial ... 

Unfortunately the configure script for the installation of the linuxwacom-driver gives me a nasty

***
*** WARNING:
*** Unable to compile wacom_drv.{o,so} without XF86 build environment
*** or Xorg SDK.
*** wacom_drv.o will not be built
***

Which is by now growing pretty frustrating, since I spent the whole day trying to fix this problem.
But the time may not be entirely lost - for I found out, that there is no such thing as a  xorg-x11-sdk - it's x-window-system-dev.

Unfortunately the problem is not yet solved, because the package seems to be a phantom. Results from rpmseek.com e.g. linked into oblivion, synaptic didn't even find anything,  neither did aptitude. By the way - wanna see a broken link? here we go:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fx-window-system-dev_6.8.2-10.4_i386.deb&md5sum=7141f0909f1ee6ee5d248d989e4017a8&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fx-window-system-dev_6.8.2-10.4_i386.deb&md5sum=7141f0909f1ee6ee5d248d989e4017a8&arch=i386&type=security)

Unfortunately the removal of the filename after the last slash revealed no usable dev-package. I already reported it to the webmaster. 

Really the whole world seems to link to [http://de.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x-window-system-dev_6.8.2-10.4_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x-window-system-dev_6.8.2-10.4_i386.deb)  
But it is nothing there. 
:(

If anybody could tell me where to find it I would be extremely happy and thankful.

---

