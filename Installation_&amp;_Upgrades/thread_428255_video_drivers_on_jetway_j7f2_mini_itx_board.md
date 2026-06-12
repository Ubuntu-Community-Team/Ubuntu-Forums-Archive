---
title: "video drivers on jetway j7f2 mini itx board"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by jhewer on 2007-04-30
hi there,

i recently installed kubuntu feisty on my Jetway J7F2 Mini ITX system (VIA C7 processor, CN700 chipset), and by default the VESA video driver is being used.  however, i'm having some problems with this...

by default, the resolution was 1280x1024 which was great for my LCD monitor, but i then turned on composite TV out on the bios (changed CRT to CRT+TV) and when kubuntu gets to the loading screen / login screen, i seem only to be able to see the top left hand corner of the screen, on both the TV and monitor.

so i switched it back to CRT only in the bios, and when to turn the resolution down thinking this might solve the problem. however. changing the resolution messed up X, so i had to reconfigure X using dpkg-reconfigure. i don't seem to be able to change the resolution without breaking it. 

so i went to the Jetway website to get the drivers for my chipset, and after attempting to install the vga drivers using the command line utility included, i got this error (n.b. the second time around, first time i forgot to capture the output)

-------- install start --------
Install VIA/S3G UniChrome familly graphic driver!
Which CPU do you use ?
1. VIA C3-2(C5N/C5P), Intel Pentium 2/3/4
C7
cp: cannot stat `///XServer/via_v4l_drv.ko': No such file or directory
cp: cannot stat `///XServer/videodev.ko': No such file or directory
cp: target `/usr/X11R6/lib/modules/drivers/' is not a directory: No such file or directory
cp: cannot stat `///XServer/via.ko': No such file or directory
cp: cannot stat `///XServer/agpgart.ko': No such file or directory
cp: cannot stat `///XServer/via-agp.ko': No such file or directory
cp: cannot stat `///XServer/libddmpeg.so': No such file or directory
sed: can't read /etc/modprobe.conf: No such file or directory
sed: can't read /etc/rc.d/rc.local: No such file or directory
cp: cannot create regular file `/etc/rc.d/rc.local': No such file or directory
sed: can't read /etc/rc.d/rc.local: No such file or directory
cp: cannot create regular file `/etc/rc.d/rc.local': No such file or directory
cp: cannot create regular file `/etc/rc.d/rc.local': No such file or directory
ERROR: Removing 'via_agp': Resource temporarily unavailable
ERROR: Removing 'agpgart': Resource temporarily unavailable
insmod: error inserting '/lib/modules/2.6.20-15-generic/kernel/drivers/char/agp/agpgart.ko': -1 File exists
insmod: error inserting '/lib/modules/2.6.20-15-generic/kernel/drivers/char/agp/via-agp.ko': -1 File exists
FATAL: Module via_v4l_drv not found.
Now start to install VIA/S3G display utility...

Warning, system cannot find the /usr/X11R6/lib/libXv.so.1.0 file.
Please install XFree86-libs RPM package first.
You can find the package in the installation CD.

Abort, the utility is not installed.
------------------------------- 

I checked the ubuntu package list for feisty, and XFree86-libs isn't listed.  Theres a bunch of otehr errors in the above output too.  Any ideas?

Thanks,
Jon

---

### Post by jhewer on 2007-04-30
just read about the OpenChrome drivers... anyone tried these out?

thanks

---

### Post by Flecko on 2008-02-06
Depending on which version of Ubuntu you're using, the openchrome drivers are probably already built in.

Install the xorg-xserver-openchrome(I think thats the name of the package) package and install the mesa-dri package. Then switch your video driver over to either openchrome or via and all should work well.

---

