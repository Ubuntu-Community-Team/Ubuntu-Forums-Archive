---
title: "Gconf removal errors"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by eljaco on 2008-06-12
Hi. I've been trying to remove some files on my computer to make space on my hard drive and I think I did something that made the Ubuntu gods angry. For some reason, whenever I log in under Gnome, it shows up some errors about gconf2 and nothing happens (no desktop icons or anything, just the blank brown screen.) I can log in under KDE just fine and I only get one of the gconf errors. Can someone help me out of this rut? See below for the problem I encounter:

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
78 not fully installed or removed.
Need to get 0B/2850kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglade2-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dictionaries-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `x11-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libopencdk10' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.
292190 files and directories currently installed.)
Preparing to replace gnome-applets 2.22.2-0ubuntu1 (using .../gnome-applets_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...

(gconftool-2:8215): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8215): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-6s37kd/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-6s37kd/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: warning - old post-removal script returned error exit status 250
dpkg - trying script from the new package instead ...

(gconftool-2:8219): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8219): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-rzzlkS/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-rzzlkS/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.22.2-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 250
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 106, in <module>
    defaults_files = os.listdir(defaults_dir)
OSError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace gnome-power-manager 2.22.1-1ubuntu4 (using .../gnome-power-manager_2.22.1-1ubuntu4_i386.deb) ...
Unpacking replacement gnome-power-manager ...

(gconftool-2:8235): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8235): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-AKViig/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-AKViig/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: warning - old post-removal script returned error exit status 250
dpkg - trying script from the new package instead ...

(gconftool-2:8239): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8239): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-6wjeh8/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-6wjeh8/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: error processing /var/cache/apt/archives/gnome-power-manager_2.22.1-1ubuntu4_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 250
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 106, in <module>
    defaults_files = os.listdir(defaults_dir)
OSError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace gnome-session 2.22.1.1-0ubuntu2 (using .../gnome-session_2.22.1.1-0ubuntu2_i386.deb) ...
Unpacking replacement gnome-session ...

(gconftool-2:8255): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8255): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-FfI8ng/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-FfI8ng/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: warning - old post-removal script returned error exit status 250
dpkg - trying script from the new package instead ...

(gconftool-2:8259): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8259): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-ZC55RP/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-ZC55RP/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: error processing /var/cache/apt/archives/gnome-session_2.22.1.1-0ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 250
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 106, in <module>
    defaults_files = os.listdir(defaults_dir)
OSError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace serpentine 0.9-5ubuntu2 (using .../serpentine_0.9-5ubuntu2_all.deb) ...
Unpacking replacement serpentine ...

(gconftool-2:8280): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8280): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-7_k4YT/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-7_k4YT/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: warning - old post-removal script returned error exit status 250
dpkg - trying script from the new package instead ...

(gconftool-2:8284): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:8284): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-1GmxTD/gconf": Failed: Couldn't locate backend module for `xml:merged:/tmp/gconf-1GmxTD/gconf'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: error processing /var/cache/apt/archives/serpentine_0.9-5ubuntu2_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 250
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 106, in <module>
    defaults_files = os.listdir(defaults_dir)
OSError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets_2.22.2-0ubuntu1_i386.deb
 /var/cache/apt/archives/gnome-power-manager_2.22.1-1ubuntu4_i386.deb
 /var/cache/apt/archives/gnome-session_2.22.1.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/serpentine_0.9-5ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help will be appreciated. Thanks!

---

### Post by eljaco on 2008-06-13
In case it helps, here's some more info:

```
~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-vfs2.0-cil:
 libgnome-vfs2.0-cil depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-vfs2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-gnome:
 policykit-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing policykit-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdl-1-0:
 libgdl-1-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgdl-1-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgdl-1-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on libgdl-1-0; however:
  Package libgdl-1-0 is not configured yet.
 python-gnome2-extras depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-extras depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2.0-cil:
 libgnome2.0-cil depends on libgnome-vfs2.0-cil (>= 2.20.0); however:
  Package libgnome-vfs2.0-cil is not configured yet.
 libgnome2.0-cil depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnome2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-3 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-panel depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-panel depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-panel depends on libgweather1; however:
  Package libgweather1 is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser10:
 libtotem-plparser10 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-gnomevfs:
 gstreamer0.10-gnomevfs depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gstreamer0.10-gnomevfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-perl:
 libgnome2-perl depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome2-perl depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnome2-perl depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome2-perl depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-7 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-9 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 2.22.2); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 2.22.2); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 2.22.2); however:
  Package libedata-cal1.2-6 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgoffice-0-6:
 libgoffice-0-6 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgoffice-0-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgoffice-0-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.14 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.14 depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2-desktop depends on libebook1.2-9 (>= 2.21.92); however:
  Package libebook1.2-9 is not configured yet.
 python-gnome2-desktop depends on libecal1.2-7 (>= 2.21.92); however:
  Package libecal1.2-7 is not configured yet.
 python-gnome2-desktop depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 python-gnome2-desktop depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2-desktop depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 python-gnome2-desktop depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
 python-gnome2-desktop depends on libtotem-plparser10 (>= 2.21.92); however:
  Package libtotem-plparser10 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-vfs-perl:
 libgnome2-vfs-perl depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-vfs-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libeel2-2:
 libeel2-2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libeel2-2 depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 libeel2-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libeel2-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libeel2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libeel2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-gecko:
 epiphany-gecko depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 epiphany-gecko depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 epiphany-gecko depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 epiphany-gecko depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 epiphany-gecko depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing epiphany-gecko (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 libedataserverui1.2-8 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libedataserverui1.2-8 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-9 (>= 2.22.1.1); however:
  Package libebook1.2-9 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on python-gnome2 (>= 2.12.4-1); however:
  Package python-gnome2 is not configured yet.
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-11:
 libcamel1.2-11 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libcamel1.2-11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdl-gnome-1-0:
 libgdl-gnome-1-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgdl-1-0; however:
  Package libgdl-1-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgdl-gnome-1-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgsf-gnome-1-114:
 libgsf-gnome-1-114 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgsf-gnome-1-114 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libslab0:
 libslab0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libslab0 depends on libeel2-2 (>= 2.21.90); however:
  Package libeel2-2 is not configured yet.
 libslab0 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libslab0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libslab0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libslab0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libslab0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-control-center
 libgnomevfs2-extra
 libgnomevfs2-0
 nautilus
 libgtkhtml3.14-19
 xulrunner-1.9-gnome-support
 libedata-book1.2-2
 libedata-cal1.2-6
 libgnome-vfs2.0-cil
 libgnome2-0
 policykit-gnome
 libgdl-1-0
 python-gnome2-extras
 libbonoboui2-0
 python-gnome2
 libgnome2.0-cil
 libgweather1
 libexchange-storage1.2-3
 gnome-panel
 libgnomeui-0
 libtotem-plparser10
 gstreamer0.10-gnomevfs
 libgnome-window-settings1
 libgnome2-perl
 libecal1.2-7
 libebook1.2-9
 evolution-data-server
 libpanel-applet2-0
 libgoffice-0-6
 firefox-3.0-gnome-support
 libgnome-desktop-2
 gtkhtml3.14
 python-gnome2-desktop
 libgnome2-vfs-perl
 libeel2-2
 epiphany-gecko
 libedataserverui1.2-8
 deskbar-applet
 libcamel1.2-11
 libgdl-gnome-1-0
 libgsf-gnome-1-114
 libslab0
 firefox-gnome-support
 liblpint-bonobo0
```

---

