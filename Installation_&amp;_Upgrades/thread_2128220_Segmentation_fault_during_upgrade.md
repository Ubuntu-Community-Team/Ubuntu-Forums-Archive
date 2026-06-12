---
title: "Segmentation fault during upgrade"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by handimanmark on 2013-03-22
Hello, good day I hope this finds you well. 

I seem to have a segmentation fualt when using sudo apt-get -f install after having already tried update, upgrade, clean, autoclean and autoremove. The following code is where I'm stuck at; any help would be much appreciated.

```
mark@R2D2:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
The following packages will be upgraded:
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
3 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
73 not fully installed or removed.
Need to get 0 B/126 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 315544 files and directories currently installed.)
Preparing to replace python-aptdaemon.pkcompat 0.43+bzr805-0ubuntu7  (using .../python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb) ...
Segmentation fault (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault (core dumped)
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace python-aptdaemon.gtk3widgets 0.43+bzr805-0ubuntu7  (using .../python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb)  ...
Segmentation fault (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault (core dumped)
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Preparing to replace python-aptdaemon 0.43+bzr805-0ubuntu7 (using .../python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb) ...
Segmentation fault (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault (core dumped)
dpkg: error processing /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
No apport report written because MaxReports is reached already
                                                              Segmentation fault (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139
Errors were encountered while processing:
 /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb
 /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb
 /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The following is also returned when I
sudo tail /var/log/apt/term.log|tr \\r \\n

```
dpkg: error processing /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb (--unpack):

 subprocess new pre-removal script returned error exit status 139

Segmentation fault (core dumped)

dpkg: error while cleaning up:

 subprocess installed post-installation script returned error exit status 139

Errors were encountered while processing:

 /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb

 /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb

 /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb

Log ended: 2013-03-22  10:04:01
```

Any suggestions would be helpful please as I am still a newbie
precise 12.04

---

### Post by |{urse on 2013-03-22
[COLOR=#4B5D67][FONT=Verdana][B]Try this:

sudo cp /var/lib/dpkg/status /var/log/dpkg/status.old[/B][/FONT][/COLOR]
[COLOR=#4B5D67][FONT=Verdana]**gksudo gedit /var/lib/dpkg/status**[/FONT][/COLOR]
[COLOR=#4B5D67][FONT=Verdana]Here comes the dicey part. Search for the package causing all this brouhaha and delete its entry. Please be very careful here and make sure you leave a blank line between the package entries below or above the deleted package entry. Here are screenshots of my file before and after selecting the appropriate package description entry.[/FONT][/COLOR]
[CENTER][COLOR=#4B5D67][FONT=Verdana][COLOR=#000000][FONT= ][[IMG]http://odzangba.files.wordpress.com/2009/10/screenshot-status-b4.png?w=500&h=375[/IMG]]("http://odzangba.files.wordpress.com/2009/10/screenshot-status-b4.png")[[IMG]http://odzangba.files.wordpress.com/2009/10/screenshot-status-after.png?w=500&h=375[/IMG]]("http://odzangba.files.wordpress.com/2009/10/screenshot-status-after.png")[/FONT][/COLOR][/FONT][/COLOR][/CENTER][COLOR=#4B5D67][FONT=Verdana]If you did this right you should be able to open Synaptic and remove the offending package (if you don&#8217;t want it any more) or re-install it.I don&#8217;t understand why the developers couldn&#8217;t cook up a more graceful way for dpkg to show its displeasure.

From: [http://odzangba.wordpress.com/2009/10/14/how-to-fix-%E2%80%9Csubprocess-pre-removal-script-returned-error-exit-status-2%E2%80%B3-error/]("http://odzangba.wordpress.com/2009/10/14/how-to-fix-%E2%80%9Csubprocess-pre-removal-script-returned-error-exit-status-2%E2%80%B3-error/")[/FONT][/COLOR]

---

### Post by schragge on 2013-03-22
Ouch, no, please do not mess around with */var/lib/dpkg/status*! At least, try first to display the information from it pertaining to the aforementioned packages, and post it here:
```
dpkg -s python-aptdaemon.pkcompat
```
```
dpkg -s python-aptdaemon.gtk3widgets
```

---

### Post by handimanmark on 2013-03-22
Thank-you for your help/suggestion.

dpkg -s python-aptdaemon.pkcompat

```
Package: python-aptdaemon.pkcompat
Status: install reinstreq half-configured
Priority: extra
Section: python
Installed-Size: 212
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: aptdaemon
Version: 0.43+bzr805-0ubuntu7
Config-Version: 0.43+bzr805-0ubuntu7
Depends: python2.7, python (>= 2.7.1-0ubuntu2), python (<< 2.8), python-aptdaemon (= 0.43+bzr805-0ubuntu7), python-packagekit
Conflicts: packagekit
Conffiles:
 /etc/dbus-1/system.d/org.freedesktop.PackageKit-aptd.conf da1bbf80a8f31fa274c49b6e881da88d
Description: PackageKit compatibilty for AptDaemon
 Aptdaemon is a transaction based package management daemon. It allows
 normal users to perform package management tasks, e.g. refreshing the
 cache, upgrading the system, installing or removing software packages.
 .
 This package adds a PackageKit DBus interface to AptDaemon.
Homepage: https://launchpad.net/aptdaemon
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Python-Version: 2.7
```

dpkg -s python-aptdaemon.gtk3widgets

```
Package: python-aptdaemon.gtk3widgets
Status: install reinstreq half-configured
Priority: extra
Section: python
Installed-Size: 115
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: aptdaemon
Version: 0.43+bzr805-0ubuntu7
Config-Version: 0.43+bzr805-0ubuntu7
Replaces: python-aptdaemon-gtk (<< 0.41+bzr582-0ubuntu1)
Depends: python2.7, python (>= 2.7.1-0ubuntu2), python (<< 2.8), python-aptdaemon (= 0.43+bzr805-0ubuntu7), python-gi, gir1.2-gtk-3.0, gir1.2-vte-2.90, aptdaemon-data
Conflicts: python-aptdaemon-gtk (<< 0.41+bzr582-0ubuntu1)
Description: Python GTK+ 3 widgets to run an aptdaemon client
 Aptdaemon is a transaction based package management daemon. It allows
 normal users to perform package management tasks, e.g. refreshing the
 cache, upgrading the system, installing or removing software packages.
 .
 This package provides the Python GTK+ 3 widgets to implement a fully
 working graphical client. The widgets can be used to initiate, to
 monitor and to control a transaction. The API is not stable yet.
Homepage: https://launchpad.net/aptdaemon
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Python-Version: 2.7
```

---

### Post by handimanmark on 2013-03-22
This error message from Synaptic Package Manager when attempting to fix broken python packages:

E: /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu8_all.deb: subprocess new pre-removal script returned error exit status 139
E: /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu8_all.deb: subprocess new pre-removal script returned error exit status 139
E: /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu8_all.deb: subprocess new pre-removal script returned error exit status 139

The dreaded "error exit status 139", what ever that means. Any other help would be very much appreciated.

Thank-you L{urse for your suggestion, I'll try the simple first though, being a newbie.

---

### Post by handimanmark on 2013-03-22
This while attempting to upgrade through Synaptic Package Manager:

```
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up update-notifier-common (0.119ubuntu8.6) ...
Segmentation fault (core dumped)
dpkg: error processing update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 139
Setting up linux-image-generic-pae (3.2.0.39.47) ...
Setting up linux-headers-3.2.0-39-generic-pae (3.2.0-39.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-generic-pae (3.2.0.39.47) ...
Setting up linux-generic-pae (3.2.0.39.47) ...
dpkg: dependency problems prevent configuration of gstreamer0.10-gconf:
 gstreamer0.10-gconf depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-gconf (--configure):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic-pae
Errors were encountered while processing:
 python-aptdaemon
 python-aptdaemon.pkcompat
 python-aptdaemon.gtk3widgets
 nvidia-current
 aptdaemon
 gconf2
 network-manager-gnome
 update-notifier-common
 flashplugin-installer
 gstreamer0.10-gconf
```

---

### Post by schragge on 2013-03-22
Please, read this: [uwiki]DebuggingInstallationIssues#Segmentation_Fault_-_Exit_status_139[/uwiki]

Just in case, try
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
If it doesn't help and you still will get* exit status 139* then most probably this is a hardware issue (faulty memory module?)

---

### Post by handimanmark on 2013-03-22
Thank-you schragge

I'll run the memory test and post the results.

Doesn't sound good. This is the first release of ubuntu that has given me problems on this Dell 1700 vostro. Release 10.04 ran rock solid even with wine and autocad running. 

Can Ram go bad over time?

---

### Post by |{urse on 2013-03-22
Absolutely, bits can go bad at the drop of a hat. Out of curiousity Scragge, why is that wrong? I've ended up having to edit my /dpkg/status every time I've gotten a persisting ' [COLOR=#000000][FONT=Ubuntu Mono]dpkg: warning: subprocess old pre-removal script returned error exit status 139'
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]
And really assuming it's bad ram isn't far off at all. ^^ Hopefully that's the real issue here.

"If the installation failed with no reason with an exit status 139, that the configuration script is trivial and there is no other report of this kind for that package, then this is very likely a memory corruption error.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]The error from the term.log will show something like this:[/FONT][/COLOR]

Setting up python-dateutil (1.4.1-2) ...Segmentation faultdpkg: error processing python-dateutil (--configure): subprocess post-installation script returned error exit status 139[COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]There is not much we can do except the advice below:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][TABLE]
[TR]
[TD]Thanks for your report.

This looks like a hardware issue. Could you run memtest on your system? (boot a live CD / USB key and select test memory)
[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]The reporter will most of the time says that the test reports error. If so, then close the report.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]**Note** : an exit status 139 can also appear on other scenarios that aren't related to faulty memory modules. For example, if you install a Hardy guest on a Lenny host using Xen, and then try an apt-get upgrade on the Hardy guest, that will fail with a segfault and an exit status 139 if you forget to disable /lib/tls as advised in the [Xen Faq]("http://wiki.xensource.com/xenwiki/XenFaq")"


[/FONT][/COLOR]

---

### Post by schragge on 2013-03-22
> **|{urse said:**
> Out of curiousity Scragge, why is that wrong? I've ended up having to edit my /dpkg/status every time I've gotten a persisting ' dpkg: warning: subprocess old pre-removal script returned error exit status 139' There's nothing wrong with editing the */var/lib/dpkg/status* per se. It's just not the procedure I would recommend to a newbie unless I'm pretty sure the dpkg status data actually got corrupted. But *segmentation fault* aka *exit status 139* aka *memory fault* can mean pretty much anything: a faulty memory module, a process running out of memory, a damaged .deb file, a buggy postinst script, a program linked against wrong library version, and so on. So far, *dpkg -s* successfully parses */var/lib/dpkg/status* and the displayed records for the packages in question don't look wrong. Sure, the packages have status *install reinstreq half-configured*, but it's to be expected after installation aborted with segmentation fault.

BTW the article you linked deals with *exit status 2* when trying to *remove* a package. In this situation, deleting the package record from */var/lib/dpkg/status* would certainly help. But even then instead of editing the file manually, I'd try to locate and remove the record with sed.

The following should give the same output as *dpkg -s [COLOR=blue]package_name[/COLOR]*:
```
sed -n '/^Package: *[COLOR=blue]package_name[/COLOR]$/,/^$/p' /var/lib/dpkg/status
``` If it does, you can delete the record with
```
sudo sed -i '/^Package: *[COLOR=blue]package_name[/COLOR]$/,/^$/d' /var/lib/dpkg/status
```

---

### Post by handimanmark on 2013-03-22
Hello schragge,

I started a Live Session with the 12.04.1 version I had on a flash drive and ran the Systems Test. The memory part uf the test reported that it passed. Since I've got some time today, I'm backing up everything and freshly installing the 64 bit desktop version of 12.04.2 LTS on this box. I already have the 64bit version running on two other boxes without any problems. Intel says this Core2Duo is 64 bit architecture so I'm going to give it a try. I just hope my 32bit version of AutoCad will run inside wine under the 64 bit version of 12.04.2 Ubuntu.

Thank-you for all of your suggestions and have a great day.

---

### Post by handimanmark on 2013-03-25
Hello again,

The saga continues... I was finally able to reformat and install a fresh copy of ubunutu 12.04.2 LTS on this Dell Vostro 1700 after experiencing "kernel panic" when attempting to do so from a Live Session on a usb flash drive. I was finally able to burn an error free Live CD and install the amd64 desktop version. Now I have no internet connection. Neither the Broadcom NIC driver BCM 4411 or the Wireless Driver BCM 4311 are working; therefore no internet at all.

I was able to copy over the compat-wireless-2.6.tar.bz2, compile the B43 driver and install it. After restart though the driver is "active but not currently in use". 

Help please.

---

