---
title: "[SOLVED] Adobe flash plugin problem"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by trendyabinash on 2008-11-19
My firefox of ubuntu 8.04
is not able to run adobe flash contents
it is saying that firefox requires plugin and showing flash plugin but after installation also it is again giving the same message that it requires plugin

---

### Post by aysiu on 2008-11-19
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo updatedb
locate flash
uname -m
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
``` Warning: the first command may take a few minutes to execute.

---

### Post by trendyabinash on 2008-11-19
This is what I got, sorry I didn't prefer to use "sudo updatedb"
as my net connection is slow
It will take a lot of time to update my system.
```
trendyabinash@abinash-desktop:~$ locate flash
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/usr/bin/btcflash
/usr/lib/openoffice/program/libflash680li.so
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/share/app-install/icons/flashblock.xpm
/usr/share/icons/HighContrastLargePrintInverse/48x48/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/Human/16x16/devices/media-flash.png
/usr/share/icons/Human/22x22/devices/media-flash-cf.png
/usr/share/icons/Human/22x22/devices/media-flash.png
/usr/share/icons/Human/24x24/devices/media-flash-cf.png
/usr/share/icons/Human/24x24/devices/media-flash-ms.png
/usr/share/icons/Human/24x24/devices/media-flash.png
/usr/share/icons/Human/48x48/devices/media-flash-cf.png
/usr/share/icons/Human/48x48/devices/media-flash-ms.png
/usr/share/icons/Human/48x48/devices/media-flash.png
/usr/share/icons/Human/scalable/devices/media-flash-cf.svg
/usr/share/icons/Human/scalable/devices/media-flash-ms.svg
/usr/share/icons/Human/scalable/devices/media-flash.svg
/usr/share/icons/gnome/16x16/devices/media-flash.png
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/22x22/devices/media-flash.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/24x24/devices/media-flash.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/32x32/devices/media-flash.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/scalable/devices/media-flash.svg
/usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-x-shockwave-flash.svg
/usr/share/man/man8/btcflash.8.gz
/usr/share/mime/application/x-flash-video.xml
/usr/share/mime/application/x-shockwave-flash.xml
/usr/src/linux-headers-2.6.24-19/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-19/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-19/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-19/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-19/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-19/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-19/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/scx200/docflash.h
trendyabinash@abinash-desktop:~$ uname -m
i686
trendyabinash@abinash-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
trendyabinash@abinash-desktop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.124.0ubuntu2
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from www.adobe.com.  The distribution license of the Adobe flash
 plugin is available at www.adobe.com.  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: http://wiki.ubuntu.com/FlashPlayer9
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
trendyabinash@abinash-desktop:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
trendyabinash@abinash-desktop:~$ dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 176
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.6.0-2ubuntu1
Replaces: swf-player
Provides: swf-player
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-1), libcairo2 (>= 1.5.14), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.12.0), liboil0.3, libpango1.0-0 (>= 1.20.0), libswfdec-0.6-90
Conflicts: swf-player
Description: Mozilla plugin for SWF files (Macromedia Flash)
 A GTK+ and swfdec based Mozilla plugin for SWF files,
 commonly known as Macromedia Flash animations.
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Swfdec player for Adobe/Macromedia Flash
Original-Maintainer: Santiago Garcia Mantinan <manty@debian.org>
trendyabinash@abinash-desktop:~$ 

```

---

### Post by aysiu on 2008-11-19
```
sudo updatedb
``` has nothing to do with your internet connection. It just refreshes the list of files on your computer. It may help if you run ```
sudo updatedb
locate flash
``` again but based on only the latter output, I'd say it's possible that running this command alone and restarting your web browser may fix the problem: ```
sudo apt-get remove swfdec-mozilla
``` If it doesn't, please run those first two commands and post the output here.

---

### Post by trendyabinash on 2008-11-19
Thank you so much sir the above mentioned step worked perfectly fine.

Can you please explain me what problem exactly I was facing???

---

### Post by aysiu on 2008-11-19
Having the SWFdec or Gnash plugin also installed pretty much overrides the Adobe Flash plugin.

So that command just removed the SWFdec plugin.

---

### Post by CheshireMac on 2008-11-19
Howdy howdy. 
I'm experiencing the same problem, running Hardy. I just installed again due to a screw up with Windows 7 . . . don't bother just yet. ;) . . . anyhow, I put in the command to remove the SWF package like stated above, but that didn't do the trick either. So I put in the other commands: [code]mac@Mac1:~$ sudo updatedb
mac@Mac1:~$ locate flash
locate: can not open `/var/lib/mlocate/mlocate.db': Permission denied
[/code}
I'm a little confused because I've never had this problem in the past. It's always been a matter of clicking my way through the install process for Flash. 
Any thoughts?

---

### Post by CheshireMac on 2008-11-19
Still haven't been able to get flash to work, after installing it through Synaptic and Firefox a couple different ways. Still tells me it's installed, but refuses to work. Websites are still prompting me to download Flash player.

---

### Post by trendyabinash on 2008-12-09
Bro I have marked this topic as SOLVED may be thats the reason no one is replying here

---

