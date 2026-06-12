---
title: "While upgrading to 10.04 FGLRX failed to install, Now can't purge it?"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by Col-1023 on 2010-09-21
I've just upgraded from ubuntu 9.10 to 10.04 64 bit, and everything went well except for the fglrx driver installation, which failed.

I've checked the troubleshooting guide and tried to purge the drivers, with only partial success.

When i type  dpkg -l '*fglrx*'

I get this,

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pH  fglrx          2:8.723.1-0ubu Video driver for the ATI graphics accelerato
un  fglrx-amdcccle <none>         (no description available)
un  fglrx-control  <none>         (no description available)
un  fglrx-control- <none>         (no description available)
un  fglrx-kernel-s <none>         (no description available)
un  fglrx-modalias <none>         (no description available)
un  xorg-driver-fg <none>         (no description available)

then, locate fglrx

gives

/etc/X11/xorg.conf.fglrx-0
/etc/acpi/fglrx-powermode.sh
/etc/acpi/fglrx-powermode.sh.dpkg-new
/etc/acpi/events/fglrx-ac-aticonfig
/etc/acpi/events/fglrx-ac-aticonfig.dpkg-new
/etc/acpi/events/fglrx-lid-aticonfig
/etc/acpi/events/fglrx-lid-aticonfig.dpkg-new
/etc/default/xorg-driver-fglrx
/etc/modprobe.d/blacklist-fglrx.conf
/home/david/Public/fglrxinfo printout
/home/david/Public/Recorded/fglrxinfo printout
/lib/fglrx
/usr/bin/fglrx_xgamma
/usr/bin/fglrxinfo
/usr/lib/fglrx
/usr/lib/libfglrx_dm.so.1
/usr/lib/libfglrx_dm.so.1.0
/usr/lib/libfglrx_gamma.so.1
/usr/lib/libfglrx_gamma.so.1.0
/usr/lib/libfglrx_tvout.so.1
/usr/lib/libfglrx_tvout.so.1.0
/usr/lib/dri/fglrx_dri.so
/usr/lib/fglrx/10fglrx
/usr/lib/fglrx/bin
/usr/lib/fglrx/dri
/usr/lib/fglrx/etc
/usr/lib/fglrx/ld.so.conf
/usr/lib/fglrx/libAMDXvBA.cap
/usr/lib/fglrx/libAMDXvBA.so.1
/usr/lib/fglrx/libAMDXvBA.so.1.0
/usr/lib/fglrx/libGL.so
/usr/lib/fglrx/libGL.so.1
/usr/lib/fglrx/libGL.so.1.2
/usr/lib/fglrx/libXvBAW.so.1.0
/usr/lib/fglrx/libatiadlxx.so
/usr/lib/fglrx/libaticalcl.so
/usr/lib/fglrx/libaticaldd.so
/usr/lib/fglrx/libaticalrt.so
/usr/lib/fglrx/libatiuki.so.1
/usr/lib/fglrx/libatiuki.so.1.0
/usr/lib/fglrx/libfglrx_dm.so.1
/usr/lib/fglrx/libfglrx_dm.so.1.0
/usr/lib/fglrx/libfglrx_gamma.so.1
/usr/lib/fglrx/libfglrx_gamma.so.1.0
/usr/lib/fglrx/libfglrx_pp.so.1
/usr/lib/fglrx/libfglrx_tvout.so.1
/usr/lib/fglrx/libglx.so.xlibmesa
/usr/lib/fglrx/xorg
/usr/lib/fglrx/etc/ati
/usr/lib/fglrx/etc/ati/amdpcsdb.default
/usr/lib/fglrx/etc/ati/atiogl.xml
/usr/lib/fglrx/etc/ati/authatieventsd.sh
/usr/lib/fglrx/etc/ati/control
/usr/lib/fglrx/etc/ati/logo.xbm.example
/usr/lib/fglrx/etc/ati/logo_mask.xbm.example
/usr/lib/fglrx/etc/ati/signature
/usr/lib/xorg/modules/drivers/fglrx_drv.so
/usr/lib/xorg/modules/linux/libfglrxdrm.so
/usr/lib32/fglrx
/usr/lib32/libfglrx_dm.so.1.0
/usr/lib32/libfglrx_gamma.so.1
/usr/lib32/libfglrx_gamma.so.1.0
/usr/lib32/libfglrx_tvout.so.1
/usr/lib32/libfglrx_tvout.so.1.0
/usr/lib32/dri/fglrx_dri.so
/usr/lib32/fglrx/dri
/usr/lib32/fglrx/libAMDXvBA.so.1.0
/usr/lib32/fglrx/libGL.so.1.2
/usr/lib32/fglrx/libXvBAW.so.1.0
/usr/lib32/fglrx/libatiadlxx.so
/usr/lib32/fglrx/libaticalcl.so
/usr/lib32/fglrx/libaticaldd.so
/usr/lib32/fglrx/libaticalrt.so
/usr/lib32/fglrx/libatiuki.so.1
/usr/lib32/fglrx/libatiuki.so.1.0
/usr/lib32/fglrx/libfglrx_dm.so.1.0
/usr/lib32/fglrx/libfglrx_gamma.so.1.0
/usr/share/fglrx
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/doc/fglrx
/usr/share/doc/fglrx-amdcccle
/usr/share/doc/fglrx-kernel-source
/usr/share/doc/fglrx-modaliases
/usr/share/doc/xorg-driver-fglrx
/usr/share/jockey/handlers/fglrx.py
/usr/share/jockey/modaliases/fglrx-modules.alias.override
/usr/share/lintian/overrides/fglrx
/usr/share/lintian/overrides/fglrx-amdcccle
/usr/share/lintian/overrides/xorg-driver-fglrx
/usr/src/fglrx-8.723.1
/var/cache/apt/archives/fglrx-amdcccle_2%3a8.723.1-0ubuntu4_amd64.deb
/var/cache/apt/archives/fglrx-kernel-source_2%3a8.723.1-0ubuntu4_amd64.deb
/var/cache/apt/archives/fglrx-modaliases_2%3a8.723.1-0ubuntu4_amd64.deb
/var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_amd64.deb
/var/cache/apt/archives/xorg-driver-fglrx_2%3a8.723.1-0ubuntu4_amd64.deb
/var/cache/jockey/fglrx.oldconf
/var/lib/dpkg/info/fglrx-amdcccle.list
/var/lib/dpkg/info/fglrx-amdcccle.md5sums
/var/lib/dpkg/info/fglrx-kernel-source.list
/var/lib/dpkg/info/fglrx-kernel-source.md5sums
/var/lib/dpkg/info/fglrx-modaliases.list
/var/lib/dpkg/info/fglrx-modaliases.md5sums
/var/lib/dpkg/info/fglrx.conffiles
/var/lib/dpkg/info/fglrx.list
/var/lib/dpkg/info/fglrx.md5sums
/var/lib/dpkg/info/fglrx.postinst
/var/lib/dpkg/info/fglrx.postrm
/var/lib/dpkg/info/fglrx.preinst
/var/lib/dpkg/info/fglrx.prerm
/var/lib/dpkg/info/fglrx.shlibs
/var/lib/dpkg/info/xorg-driver-fglrx.conffiles
/var/lib/dpkg/info/xorg-driver-fglrx.list
/var/lib/dpkg/info/xorg-driver-fglrx.md5sums
/var/lib/dpkg/info/xorg-driver-fglrx.postinst
/var/lib/dpkg/info/xorg-driver-fglrx.postrm
/var/lib/dpkg/info/xorg-driver-fglrx.preinst
/var/lib/dpkg/info/xorg-driver-fglrx.shlibs

Trying the more aggressive removal commands,

sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

Gives this,

david@liberator:~$ sudo apt-get remove --purge fglrx*
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting xorg-driver-fglrx for regex 'fglrx*'
Note, selecting fglrx-kernel-source for regex 'fglrx*'
Note, selecting xorg-driver-fglrx-dev for regex 'fglrx*'
Note, selecting fglrx for regex 'fglrx*'
Note, selecting fglrx-driver-dev for regex 'fglrx*'
Note, selecting fglrx-control-qt2 for regex 'fglrx*'
Note, selecting fglrx-dev for regex 'fglrx*'
Note, selecting fglrx-modaliases for regex 'fglrx*'
Note, selecting xfree86-driver-fglrx-dev for regex 'fglrx*'
Note, selecting fglrx-amdcccle for regex 'fglrx*'
Note, selecting fglrx-control for regex 'fglrx*'
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 100MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 299873 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@liberator:~$ 

I noticed the package mismatch errors and the e-sub process error code 1 and searched for help

I found this threat - "subprocess post-removal script returned error exit status 2". erk. 

It suggested the command 

sudo dpkg -P kio-umountwrapper, which I modified to sudo dpkg -P fglrx

and it gave,

david@liberator:~$ sudo dpkg -P fglrx
(Reading database ... 299873 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
david@liberator:~$ 

Here Is the output from dpkg-divert --list

david@liberator:~$ dpkg-divert --list
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common
diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx
diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx
diversion of /usr/share/dbus-1/services/org.freedesktop.Notifications.service to /usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd by notify-osd
diversion of /usr/bin/screen to /usr/bin/screen.real by screen-profiles
diversion of /usr/lib/gnupg/gpgkeys_curl to /usr/lib/gnupg/gpgkeys_curl.non_curl by gnupg-curl
diversion of /usr/lib/gnupg/gpgkeys_hkp to /usr/lib/gnupg/gpgkeys_hkp.non_curl by gnupg-curl
diversion of /usr/share/gnome-games/pixmaps/slot.svg to /usr/share/gnome-games/pixmaps/slot.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/pixmaps/baize.png to /usr/share/gnome-games/pixmaps/baize.png.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg to /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg to /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg to /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg.unbranded by branding-ubuntu
david@liberator:~$ 


I also tried 

sudo aptitude update
sudo aptitude -f install

but these didn't fix the problem.

They didn't fix the problem.

The post contained a link, [http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

This along with an earlier post suggested modifying various files, which I'm worried about doing.

Any help with htis would be appreciated,

Thank You.

---

### Post by Col-1023 on 2010-09-22
Here is the section of the above post which I think might be the most importent.

Removing fglrx ...
dpkg-divert: mismatch on package
when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

There seems to be a fight between fglrx and xorg-driver-fglrx.

I really need a fix for this problem, any help very much appreciated

---

### Post by Col-1023 on 2010-09-22
When I check to see if my system is still running ati drivers, I get,

david@liberator:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Mesa Project
david@liberator:~$ 

This seems to indicate that no fglrx is running, then why does my system reboot into low graphics mode, and how come 1 fglrx package is not fully installed or removed?

---

### Post by Col-1023 on 2010-09-22
I loaded the file /etc/X11/xorg.conf.fglrx-0

and found this.

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


When I loaded /etc/X11/xorg.conf, I got this,

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Both xorg.conf files are full of ati and fglrx info, even though the system says the driver waasn't activated, didn't install properly, and now since I've tried to uninstall it, the hardware driver app doesn't even show it as available.

I hope this extra info can help to resolve my problem.

---

### Post by Col-1023 on 2010-09-22
According to the following post by Toon Macharis, I should be looking for the file,  /var/lib/dpkg/info/xorg-driver-fglrx.postrm.

I don't have that file at all, however I do have, 

/var/lib/dpkg/info/fglrx.postrm.

This file contains entries which may be relevent to my diversion problem, 

 remove|purge)
        dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2 > /dev/null
        dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2 > /dev/null
        dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib/fglrx/libglx.so.xlibmesa /usr/lib/xorg/modules/extensions/libglx.so > /dev/null


So Do I Need to modify this file, or create the xorg-driver-fglrx.postrm file?

Post by toon Macharis.

 Re: "subprocess post-removal script returned error exit status 2". erk.
Hi there,

I recently had a similar problem as described in [http://ubuntuforums.org/showthread.php?t=668097](http://ubuntuforums.org/showthread.php?t=668097)

The previous post was closed for posting, so I will post my solution here, as it probably is the same problem.

first go to a command line and execute the command

dpkg-divert --list

The package I was having problems with was xorg-driver-fglrx. The output of the previous command was

...
diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx
diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx
diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx
diversion of /usr/lib32/libGL.so.1 to /usr/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx
...


The lines in the output take the form

diversion of XXX to YYY by package

in this, package is the of your package. In my case, this was xorg-driver-fglrx, in your case this would be kio-unmountwrapper

Look for the file /var/lib/dpkg/info/package.postrm
I had to look for /var/lib/dpkg/info/xorg-driver-fglrx.postrm
You will have to look for /var/lib/dpkg/info/kio-unmountwrapper.postrm

Before you make any changes to the file, it could be smart to make a back up copy.

When I opened the file xorg-driver-fglrx.postrm, it contained the lines:

...
dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1.2 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib/libGL.so.1.2 > /dev/null
...


These lines are of the form:

dpkg-diver --remove --rename --package $PKGNAME --divert YYY XXX > /dev/null


The lines in this file have to be in synch with the lines that are shown after you execute the dpkg-divert --list command. They were not, so I fixed the file /var/lib/dpkg/info/xorg-driver-fglrx.postrm to look like:

...
dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib/libGL.so.1.2 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa /usr/X11R6/lib32/libGL.so.1 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2 > /dev/null

dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.xlibmesa /usr/lib32/libGL.so.1 > /dev/null
...

After I had fixed the postrm file, I could remove my package without any problem. I hope this will work for you as well.

---

### Post by Col-1023 on 2010-09-22
locate fglrx as shown in the first post says i have these files,

/var/lib/dpkg/info/xorg-driver-fglrx.conffiles
/var/lib/dpkg/info/xorg-driver-fglrx.list
/var/lib/dpkg/info/xorg-driver-fglrx.md5sums
/var/lib/dpkg/info/xorg-driver-fglrx.postinst
/var/lib/dpkg/info/xorg-driver-fglrx.postrm
/var/lib/dpkg/info/xorg-driver-fglrx.preinst
/var/lib/dpkg/info/xorg-driver-fglrx.shlibs

I checked the var/lib/dpkg/info directory and didn't find any ot these files.

When doing a search for xorg-driver, I could only find,

a deb file of 13.8 KB in /var/cache/apt/archives

why would locate fglrx say the above files exist, if they don't?

---

### Post by crl0901 on 2010-09-22
I had this same problem, but I discovered it after trying to activate the ATI proprietary drivers in Ubuntu.  I finally just did a fresh install and decided to not activate them.  I'm using Ubuntu 10.04 x64 and have an ATI HD3200.  I don't think I've done a full system update yet, so it'll be interesting to see if I encounter the error again after updating.

---

### Post by Col-1023 on 2010-09-22
I think I have solved my problem following the instructions in this link, [http://caulfield.info/emmet/technology/linux/ubuntu/](http://caulfield.info/emmet/technology/linux/ubuntu/), provided by Soapstarjoe on the top of page 3 of this thread, [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1466085](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1466085).

I was able to remove the diversions that were causing problems, then I caould pruge fglrx.

Synaptic now marks fglrx in white, ie ready for installation, but not broken.

Hardware drivers says the ati drivers are NOT ACTIVATED.

So I'm pretty sure my problem is solved.

I won't be activating the fglrx drivers though until the problem discussed in the link [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518) provided by Veko on page 5 of the other thread, are fixed.

Thanks everyone for your help.

---

