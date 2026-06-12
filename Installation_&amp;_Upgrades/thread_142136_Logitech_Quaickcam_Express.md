---
title: "Logitech Quaickcam Express"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by R3linquish3r on 2006-03-09
Ok well I found another thread taht showed how to setup my webcam to use in Gnomemeeting. I did that and it recognized it fine but when I click to use it as a camera everything locks up and I have to reboot VIA the power button. Anyone have a clue what isn't set up right?

---

### Post by R3linquish3r on 2006-03-09
Just realized I spelled the topic title wrong. :P

---

### Post by arnieboy on 2006-03-09
[QUOTE=R3linquish3r]Just realized I spelled the topic title wrong. :P[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)
will solve your problem

---

### Post by R3linquish3r on 2006-03-09
Thx arnie got it workin now :) Woulda taken a while to find that thread.

---

### Post by R3linquish3r on 2006-03-09
Another queston. I dunno if its from a guide i was using to try and setup my cam before or not but I changed something and now I cant install with sudo apt-get. Heres what has been happening:

```
ed@EAGLE:~$ sudo apt-get install camorama
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  camorama
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/106kB of archives.
After unpacking 803kB of additional disk space will be used.

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 newline in field name `sed'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by arnieboy on 2006-03-09
[QUOTE=R3linquish3r]Another queston. I dunno if its from a guide i was using to try and setup my cam before or not but I changed something and now I cant install with sudo apt-get. Heres what has been happening:

```
ed@EAGLE:~$ sudo apt-get install camorama
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  camorama
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/106kB of archives.
After unpacking 803kB of additional disk space will be used.

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 newline in field name `sed'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```[/QUOTE]
can u paste the results of
```
cat /var/lib/dpkg/available
```
please include all newlines and spaces..

---

### Post by R3linquish3r on 2006-03-09
Its to long for one post so Ill seperate it.


```
Source: openoffice.org2
Version: 1.9.129-0.1ubuntu4
Replaces: openoffice.org2-core (<< 1.9.114)
Depends: openoffice.org2-core (>> 1.9.129), libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.1), libstdc++6 (>= 4.0.1), libstlport4.6c2
Description: OpenOffice.org office suite - spreadsheet
 OpenOffice.org is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the the spreadsheet component for OpenOffice.org,
 a full-featured office productivity suite that provides a near drop-in
 replacement for Microsoft(R) Office.

Package: libatm1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 128
Maintainer: Peter De Schrijver (p2) <p2@mind.be>
Architecture: i386
Source: linux-atm
Version: 2.4.1-17
Depends: libc6 (>= 2.3.4-1)
Conflicts: atm-tools (<< 2.4.1-6)
Description: shared library for ATM (Asynchronous Transfer Mode)
 Shared libraries needed by ATM (Asynchronous Transfer Mode) related programs
 .
 Homepage: http://linux-atm.sourceforge.net/

Package: hdparm
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 212
Maintainer: Stephen Gran <sgran@debian.org>
Architecture: i386
Version: 6.1-1ubuntu2
Replaces: apmd (<= 3.0.2-1.15)
Depends: libc6 (>= 2.3.4-1), lsb-base (>= 1.3-9ubuntu3)
Suggests: apmd
Conffiles:
 /etc/default/hdparm ee52ca27cf61d5ade54d324e5cda0ff9
 /etc/init.d/hdparm f0bd40b1c78b730481be29b28c00d8b1
 /etc/apm/event.d/20hdparm 69c0a826b29c8f40b7ca5e56e53d7f83
 /etc/hdparm.conf 96c94083d620351afcd59a03d7196075
 /etc/dev.d/block/hdparm.dev c3e17cd0f3b68706395956292d31c7bd
Description: tune hard disk parameters for high performance
 Get/set hard disk parameters for Linux IDE drives.
 Primary use is for enabling irq-unmasking and IDE multiplemode.

Package: xwd
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 72
Maintainer: Fabio M. Di Nitto <fabbione@ubuntu.com>
Architecture: i386
Version: 0.99.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.3.4-1), libice6, libsm6, libx11-6, libxext6, libxmu6, libxt6
Description: X client - xwd
 xwd is a small tool that was part of xbase-clients.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'app/xwd' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

Package: fglrx-kernel-source
Status: install ok installed
Priority: extra
Section: restricted
Installed-Size: 500
Maintainer: Aric Cyr <Aric.Cyr@gmail.com>
Architecture: i386
Source: fglrx-installer
Version: 8.22.5-1
Depends: debconf, debhelper (>= 4), make, bzip2
Recommends: module-assistant | kernel-package
Suggests: xorg-driver-fglrx
Description: Kernel module source for the ATI graphics accelerators
 Video driver for the ATI Radeon and FireGL graphics accelerators.
 .
 This package provides the kernel module build environment.

Package: tcpdump
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 620
Maintainer: Romain Francoise <rfrancoise@debian.org>
Architecture: i386
Version: 3.9.1-1ubuntu1
Depends: libc6 (>= 2.3.4-1), libpcap0.8, libssl0.9.7
Description: A powerful tool for network monitoring and data acquisition
 This program allows you to dump the traffic on a network. tcpdump
 is able to examine IPv4, ICMPv4, IPv6, ICMPv6, UDP, TCP, SNMP, AFS
 BGP, RIP, PIM, DVMRP, IGMP, SMB, OSPF, NFS and many other packet
 types.
 .
 It can be used to print out the headers of packets on a network
 interface, filter packets that match a certain expression. You can
 use this tool to track down network problems, to detect "ping attacks"
 or to monitor network activities.
 .
 Further information is available at <URL: http://www.tcpdump.org/>

Package: xserver-xorg-input-elographics
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 204
Maintainer: Ubuntu X Maintainers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: xorg
Version: 6.8.2-77
Replaces: xserver-xorg (<< 6.8.2-35)
Depends: xserver-xorg-core (>= 6.8.2-35)
Conflicts: xserver-xorg (<< 6.8.2-35)
Description: X.Org X server -- ELOGraphics input driver
 This driver for the X.Org X server (see xserver-xorg for a further description)
 provides support for ELO Graphics graphics tablets.
 .
 For more information, please see the xserver-xorg package description.

Package: gnome-icon-theme
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 12512
Maintainer: Takuo KITAME <kitame@debian.org>
Architecture: all
Version: 2.12.1-0ubuntu1
Replaces: kdebase (<< 4:3.2.2-1), gnome-panel-data (<= 2.9.91-1)
Depends: hicolor-icon-theme
Enhances: nautilus (>= 2.2)
Description: GNOME Desktop icon theme
 Icons which are used for GNOME desktop theme.

Package: vnc-common
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 184
Maintainer: Ola Lundqvist <opal@debian.org>
Architecture: i386
Source: vnc
Version: 3.3.7-7ubuntu1
Depends: libc6 (>= 2.3.4-1), perl
Pre-Depends: dpkg (>= 1.6.8)
Suggests: xvncviewer | vncviewer, vncserver
Conflicts: vnc, vnc-doc, vncserver (<< 3.3.6-1)
Conffiles:
 /etc/vnc.conf 260546716e9c4457b883e051a1c44154
Description: Virtual network computing server software
 VNC stands for Virtual Network Computing. It is, in essence, a remote
 display system which allows you to view a computing `desktop' environment
 not only on the machine where it is running, but from anywhere on the
 Internet and from a wide variety of machine architectures.
 .
 It is implemented in a client/server model. This package provides common
 utilities for the server and client packages.

Package: x11proto-randr-dev
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 68
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Architecture: all
Source: x11proto-randr
Version: 1.1-1
Replaces: libxrandr-dev (<< 6.8.2-21)
Depends: x-common
Pre-Depends: x-common (>= 1.0)
Conflicts: libxrandr-dev (<< 6.8.2-21)
Description: X11 RandR extension wire protocol
 This package provides the wire protocol for the RandR extension, used to
 change display properties such as resolution, rotation, reflection, et al,
 on the fly.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'proto/Randr' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

Package: linux-headers-2.6.12-9
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 47328
Maintainer: Ben Collins <ben.collins@ubuntu.com>
Architecture: i386
Source: linux-source-2.6.12
Version: 2.6.12-9.23
Provides: linux-headers, linux-headers-2.6
Depends: coreutils | fileutils (>= 4.0)
Description: Header files related to Linux kernel version 2.6.12
 This package provides kernel header files for version 2.6.12, for sites
 that want the latest kernel headers. Please read
 /usr/share/doc/linux-headers-2.6.12-9/debian.README.gz for details

Package: x11proto-kb-dev
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 180
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Architecture: all
Source: x11proto-kb
Version: 1.0+cvs.20050817-1
Replaces: libxkbfile-dev (<< 6.8.2-20)
Depends: x-common
Pre-Depends: x-common (>= 1.0)
Conflicts: libxkbfile-dev (<< 6.8.2-20)
Description: X11 XKB extension wire protocol
 This package provides the wire protocol for the XKEYBOARD extension, used to
 control all manner of options related to keyboard handling and layout in
 particular.  It does not control the addition/enabling/disabling of keyboards;
 this is done with the XINPUT extension.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'proto/KB' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

Package: libpt-plugins-v4l
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 204
Maintainer: Debian VoIP Team <pkg-voip-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: pwlib
Version: 1.8.7-1ubuntu1
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.1), libstdc++6 (>= 4.0.1), libpt-1.8.3c2 (= 1.8.7-1ubuntu1)
Description: Portable Windows Library Video Plugin for Video4Linux
 This package contains the PWLib plugin for usage with Video4Linux
 devices.  Install this package, if you want to use a video device
 that is not attached to FireWire.

Package: python-pyao
Status: install ok installed
Priority: optional
Section: interpreters
Installed-Size: 76
Maintainer: Christopher L Cheney <ccheney@debian.org>
Architecture: i386
Source: pyao
Version: 0.82-1ubuntu1
Depends: python (<< 2.5), python (>= 2.4), libao2 (>= 0.8.5), libc6 (>= 2.3.2.ds1-4)
Description: A Python interface to the Audio Output library
 This module makes the libao (Audio Output) functions available
 in Python. With this module you can write Python applications
 that use the cross platform audio output library.

Package: xvinfo
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 60
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Architecture: i386
Version: 1.0-2
Replaces: xbase-clients (<< 6.8.2-36)
Depends: libc6 (>= 2.3.4-1), libx11-6, libxext6, libxv1
Description: XVideo information
 xvinfo is a tool to output information on the current state of XVideo support
 within the server, including currently active adaptors, the settings and
 colourspaces they support, et al.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'app/xvinfo' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

Package: python2.4-libxml2
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 876
Maintainer: Debian XML/SGML Group <debian-xml-sgml-pkgs@lists.alioth.debian.org>
Architecture: i386
Source: libxml2
Version: 2.6.21-0ubuntu1
Depends: libc6 (>= 2.3.4-1), libxml2 (>= 2.6.20), python2.4
Description: Python 2.4 bindings for the GNOME XML library
 XML is a metalanguage to let you design your own markup language.
 A regular markup language defines a way to describe information in
 a certain class of documents (eg HTML). XML lets you define your
 own customized markup languages for many classes of document. It
 can do this because it's written in SGML, the international standard
 metalanguage for markup languages.
 .
 This package contains the files needed to use the GNOME XML library
 in Python programs.

Package: libgtk2.0-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 11256
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: all
Source: gtk+2.0
Version: 2.8.6-0ubuntu2.1
Replaces: libgtk1.3-common, libgtk2.0-data
Depends: libgtk2.0-0
Conflicts: libgtk1.3-common, libgtk2.0-data
Description: Common files for the GTK+ graphical user interface library
 The GTK+ is a multi-platform toolkit for creating graphical user
 interfaces. Offering a complete set of widgets, the GTK+ is suitable
 for projects ranging from small one-off tools to complete application
 suites.
 .
 This package contains the common files which the libraries need.

Package: xcursorgen
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 48
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Architecture: i386
Version: 1.0-1
Replaces: xbase-clients (<< 6.8.2-35)
Depends: libc6 (>= 2.3.4-1), libpng12-0 (>= 1.2.8rel), libx11-6, libxcursor1 (>> 1.1.2), libxrender1
Conflicts: xbase-clients (<< 6.8.2-35)
Description: X cursor generation
 xcursorgen is a tool to generate cursors for the Xcursor library from a set
 of PNG files.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'app/xcursorgen' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

Package: kde-guidance
Status: install ok installed
Priority: optional
Section: kde
Installed-Size: 1736
Maintainer: Fathi Boudra <fboudra@free.fr>
Architecture: i386
Version: 0.4.0-0ubuntu4
Depends: kdelibs4c2 (>= 4:3.4.2), libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.1), libpythonize0, libqt3-mt (>= 3:3.3.4), libstdc++6 (>= 4.0.1), libx11-6, libxext6, libxrandr2, libxrender1, libxxf86vm1, python2.4 (>= 2.3.90), python (<< 2.5), python (>= 2.4), python-kde3
Description: collection of KDE system administration tools for GNU/Linux
 Guidance currently consists of three programs designed to help you
 look after your system:
  o  userconfig - User and Group administration
  o  serviceconfig - Service/daemon administration
  o  mountconfig - Disk and filesystem administration
 .
 
```

---

### Post by R3linquish3r on 2006-03-09
```
 These tools are available in KDE Control center or can be
 run as standalone applications.

Package: ttf-punjabi-fonts
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 256
Maintainer: Soumyadip Modak <soumyadip@softhome.net>
Architecture: all
Source: ttf-indic-fonts
Version: 1:0.4.4ubuntu2
Depends: defoma
Suggests: xserver-xfree86 | xserver | xfs, x-ttcidfont-conf
Conflicts: ttf-indic-fonts (<< 1:0.4.1)
Conffiles:
 /etc/defoma/hints/ttf-punjabi-fonts.hints b1d0998dc35ff4629bdd5b49f7bc7698
Description: Free TrueType fonts for the Punjabi language
 This is a set of TrueType and OpenType fonts released under the GNU General
 Public License for the Punjabi Language.

Package: libgtksourceview1.0-0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 260
Maintainer: Andrew Lau <netsnipe@users.sourceforge.net>
Architecture: i386
Source: gtksourceview
Version: 1.4.2-0ubuntu1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.0), libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.8.0), libgnomeprint2.2-0 (>= 2.11.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.10.1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.20), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1), libgtksourceview-common (>= 1.4.2-0ubuntu1)
Description: shared libraries for the GTK+ syntax highlighting widget
 GtkSourceView is a text widget that extends the standard GTK+ 2.x text widget
 GtkTextView. It improves GtkTextView by implementing syntax highlighting and
 other features typical of a source editor.
 .
 This package contains the shared libraries required by applications to use
 this widget.
 .
 Homepage: http://gtksourceview.sourceforge.net/

Package: libhsqldb-java
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 764
Maintainer: Peter Eisentraut <petere@debian.org>
Architecture: all
Source: hsqldb
Version: 1.8.0.0-2ubuntu1
Depends: java-gcj-compat | java2-runtime, libservlet2.3-java
Suggests: java-virtual-machine, libhsqldb-java-doc
Description: Java SQL database engine
 HSQLDB is an SQL relational database engine written in Java.  It has a
 JDBC driver and supports a rich subset of SQL-92 (BNF tree format) plus
 SQL:1999 and SQL:2003 enhancements.  It offers a small, fast database
 engine that offers both in-memory and disk-based tables.  Embedded and
 server modes are available.  Additionally, it includes tools such as a
 minimal web server, in-memory query and management tools (can be run as
 applets), and a number of demonstration examples.
 .
 Web site: http://hsqldb.sourceforge.net/

Package: lshw
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 404
Maintainer: Ghe Rivero <ghe@upsa.es>
Architecture: i386
Version: 02.03-2build1
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.0-7), libstdc++6 (>= 4.0.0-7), lshw-common
Description: information about hardware configuration
 A small tool to provide detailed information on the hardware
 configuration of the machine. It can report exact memory
 configuration, firmware version, mainboard configuration, CPU version
 and speed, cache configuration, bus speed, etc. on DMI-capable x86
 systems and on some PowerPC machines (PowerMac G4 is known to work).
 .
 Information can be output in plain text, HTML or XML.

Package: evince
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 2732
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: i386
Version: 0.4.0-0ubuntu4
Provides: pdf-viewer, postscript-viewer
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libaudiofile0 (>= 0.2.3-4), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.0), libdbus-1-1 (>= 0.36.2), libdbus-glib-1-1 (>= 0.36.2), libdjvulibre15, libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgconf2-4 (>= 2.9), libgcrypt11, libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.8.0), libgnome-keyring0 (>= 0.4.3), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.11.1), libgnomeprint2.2-0 (>= 2.11.0), libgnomeprintui2.2-0 (>= 2.11.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.11.3), libgnutls11 (>= 1.0.16), libgpg-error0 (>= 1.0), libgtk2.0-0 (>= 2.8.0), libice6, libjpeg62, libkpathsea3 (>= 2.0.2-1), liblaunchpad-integration0 (>= 0.0patch26), libnautilus-extension1 (>= 2.9.1), liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.10.0), libpng12-0 (>= 1.2.8rel), libpoppler0c2 (>= 0.4.0), libpoppler0c2-glib (>= 0.4.0), libpopt0 (>= 1.7), libsm6, libstdc++6 (>= 4.0.1), libtasn1-2 (>= 0.2.8), libtiff4, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.20), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1), gconf2 (>= 2.6.2-1), gs-esp | gs
Description: Document (postscript, pdf) viewer
 Evince is a simple multi-page document viewer.  It can display and print
 PostScript (PS), Encapsulated PostScript (EPS), DJVU, DVI and Portable
 Document Format (PDF) files.
 When supported by the document, it also allows searching for text,
 copying text to the clipboard, hypertext navigation, and
 table-of-contents bookmarks.
 .
 The PDF renderer is based on XPDF.  The PS renderer uses Ghostscript.
 .
 Homepage: http://www.gnome.org/projects/evince/

Package: kdeprint
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 2360
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdebase
Version: 4:3.5.1-0ubuntu0breezy1
Replaces: kdebase (<< 4:3.0.0), kdebase-doc (<< 4:3.0.0), kdebase-data (<< 4:3.5.0)
Depends: kdelibs4c2 (>= 4:3.4.3-1), libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.1), libqt3-mt (>= 3:3.3.4), libstdc++6 (>= 4.0.1), enscript, poster, psutils
Recommends: kghostview | postscript-viewer
Suggests: khelpcenter, efax | hylafax-client | mgetty-fax
Description: print system for KDE
 This package contains the KDE printing subsystem. It can use CUPS,
 lpd-ng or the traditional lpd. It also includes support for fax and
 pdf printing.
 .
 This package is part of KDE, and a component of the KDE base module.
 See the 'kde' and 'kdebase' packages for more information.
 .
 Homepage: http://printing.kde.org

Package: liblzo1
Status: install ok installed
Priority: important
Section: libs
Installed-Size: 188
Maintainer: Peter Eisentraut <peter_e@gmx.net>
Architecture: i386
Source: lzo
Version: 1.08-2
Depends: libc6 (>= 2.3.2.ds1-4)
Conflicts: lzop (<= 1.00)
Description: data compression library
 LZO is a portable, lossless data compression library.
 It offers pretty fast compression and very fast decompression.
 Decompression requires no memory.  In addition there are slower
 compression levels achieving a quite competitive compression ratio
 while still decompressing at this very high speed.
 .
 Home page: http://www.oberhumer.com/opensource/lzo/

Package: libeel2-data
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 1232
Maintainer: Takuo KITAME <kitame@debian.org>
Architecture: all
Source: eel2
Version: 2.12.1-0ubuntu1
Recommends: libeel2-2
Description: Eazel Extensions Library - data files (for GNOME2)
 This package includes locale data and fonts for EEL.
 .
 The Eazel Extensions Library is a collection of widgets and extensions
 to many modules of the GNOME platform.  These widgets and extensions
 were developed by hackers working on Nautilus.   For the duration of
 the Nautilus 1.0 development cycle, the code was internal to Nautilus
 and its components.
 .
 This package for GNOME2

Package: libvte-common
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 984
Maintainer: Arnaud Patard <arnaud.patard@rtp-net.org>
Architecture: all
Source: vte
Version: 1:0.11.15-0ubuntu2
Replaces: libvte2 (<= 0.5.1-2)
Description: Terminal emulator widget for GTK+ 2.0 - common files
 The VTE library inserts terminal capability strings into a trie, and then
 uses it to determine if data received from a pseudo-terminal is a control
 sequence or just random data. The sample program "interpret" illustrates
 more or less what the widget sees after it filters incoming data.
 .
 This package contains internationalization files for the VTE library.

Package: libshout3
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 112
Maintainer: Jonas Smedegaard <dr@jones.dk>
Architecture: i386
Source: libshout
Version: 2.1-3
Depends: libc6 (>= 2.3.4-1), libogg0 (>= 1.1.2), libtheora0, libvorbis0a (>= 1.1.0)
Description: MP3/Ogg Vorbis broadcast streaming library
 A library for communicating with and sending data to Icecast and Icecast 2
 streaming audio servers.  It handles the socket connection, the timing of
 the data transmission, and prevents bad data from getting to the server.
 .
 Website: http://www.icecast.org/

Package: libtiff4
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 1608
Maintainer: Jay Berkenbilt <qjb@debian.org>
Architecture: i386
Source: tiff
Version: 3.7.3-1ubuntu1
Depends: libc6 (>= 2.3.4-1), libjpeg62, zlib1g (>= 1:1.2.1)
Description: Tag Image File Format (TIFF) library
 libtiff is a library providing support for the Tag Image File Format
 (TIFF), a widely used format for storing image data.  This package
 includes the shared library.

Package: gaim
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 2148
Maintainer: Robert McQueen <robot101@debian.org>
Architecture: i386
Version: 1:1.5.0-1ubuntu3
Replaces: gaim-gnome, gaim-common
Provides: gaim-gnome
Depends: gaim-data (= 1:1.5.0-1ubuntu3), libao2 (>= 0.8.6), libaspell15 (>= 0.60), libatk1.0-0 (>= 1.9.0), libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.0), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcrypt11, libglib2.0-0 (>= 2.8.0), libgnutls11 (>= 1.0.16), libgtk2.0-0 (>= 2.8.0), libgtkspell0 (>= 2.0.2), libice6, liblaunchpad-integration0 (>= 0.0patch26), libpango1.0-0 (>= 1.10.0), libpng12-0 (>= 1.2.8rel), libsm6, libstartup-notification0 (>= 0.8-1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxss1, zlib1g (>= 1:1.2.1)
Suggests: gnome-panel (>= 2.1) | kicker (>= 3.1) | docker, evolution-data-server (>= 1.2.0), libzephyr3, tcl8.4 (>= 8.4.5), tk8.4 (>= 8.4.5)
Conflicts: gaim-gnome, gaim-common
Description: multi-protocol instant messaging client
 Gaim is a modular Instant Messaging client capable of using AIM, ICQ,
 Yahoo!, MSN, IRC, Jabber, Napster, Zephyr, and Gadu-Gadu all at once.
 It is written using GTK+ and is licensed under the GPL.
 .
 As the name suggests, it was originally designed for using AOL's
 Instant Messenger service (you can sign up at http://www.aim.aol.com/).
 Consequently it contains many of the same features as AOL's IM client,
 as well as incorporating many new and unique features, such as the
 multiple protocol support.
 .
 Gaim used to ship a gaim-gnome package which contained an applet for
 the GNOME 1.4 panel. This has been replaced in favor of a tray
 icon plugin, contained in this version. To see it in GNOME 2, use
 the Notification Area applet (included in gnome-panel versions 2.1 and
 later), or in KDE 3.1 it should appear in the Kicker's system tray.
 Users of other window managers should investigate docker, the WM dock
 app.

Package: libcommons-cli-java
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 80
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 1.0-6
Depends: gij | sablevm | kaffe (>= 2:1.1.4) | java1-runtime | java2-runtime
Suggests: java-virtual-machine
Description: API for working with the command line arguments and options
 You define arguments you want to parse, parse arguments the user
 entered and then you can retrieve them like properties
 .
 Homepage: http://jakarta.apache.org/commons/cli

Package: libaudiofile0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 220
Maintainer: Daniel Kobras <kobras@debian.org>
Architecture: i386
Source: audiofile
Version: 0.2.6-6
Depends: libc6 (>= 2.3.4-1)
Description: Open-source version of SGI's audiofile library
 The audiofile library allows the processing of audio data to and from audio
 files of many common formats (currently AIFF, AIFF-C, WAVE, NeXT/Sun, BICS,
 and raw data).
 .
 This package contains the library needed to run executables using
 libaudiofile.

Package: xserver-xorg-driver-newport
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 208
Maintainer: Ubuntu X Maintainers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: xorg
Version: 6.8.2-77
Replaces: xserver-xorg (<< 6.8.2-35)
Depends: xserver-xorg-core (>= 6.8.2-35)
Conflicts: xserver-xorg (<< 6.8.2-35)
Description: X.Org X server -- Newport driver
 This driver for the X.Org X server (see xserver-xorg for a further description)
 provides support for the integrated Newport cards found in SGI Indy and
 Indy2 machines.
 .
 For more information, please see the xserver-xorg package description.

Package: beep-media-player
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 3588
Maintainer: Mathias Weyland <mathias@weyland.ch>
Architecture: i386
Version: 0.9.7.1+cvs20050803-1ubuntu1
Provides: mp3-decoder
Depends: libasound2 (>> 1.0.9), libatk1.0-0 (>= 1.9.0), libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2), libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.8.0), libgtk2.0-0 (>= 2.8.0), libid3-3.8.3c2, libogg0 (>= 1.1.2), libpango1.0-0 (>= 1.10.1), libpng12-0 (>= 1.2.8rel), libstdc++6 (>= 4.0.1), libvorbis0a (>= 1.1.0), libvorbisfile3 (>= 1.1.0), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.20), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1)
Suggests: unzip
Description: Versatile audio player that supports Winamp skins
 A player that supports Winamp skins, with a customizable interface based on
 GTK2. It has various output plugins and can read various audio formats.

Package: lynx
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 4552
Maintainer: James Troup <james@nocrew.org>
Architecture: i386
Version: 2.8.5-2ubuntu0.5.10.1
Replaces: lynx-ssl
Provides: www-browser, news-reader, lynx-ssl
Depends: libbz2-1.0, libc6 (>= 2.3.4-1), libgnutls11 (>= 1.0.16), libncursesw5 (>= 5.4-5), zlib1g (>= 1:1.2.1)
Recommends: mime-support
Conflicts: lynx-ssl
Conffiles:
 /etc/lynx.cfg b15e2a083dd7b2103e7c54f5924575fb
Description: Text-mode WWW Browser
 Lynx is a fully-featured World Wide Web (WWW) client for users
 running cursor-addressable, character-cell display devices (e.g.,
 vt100 terminals, vt100 emulators running on PCs or Macs, or any other
 "curses-oriented" display). It will display hypertext markup language
 (HTML) documents containing links to files residing on the local
 system, as well as files residing on remote systems running Gopher,
 HTTP, FTP, WAIS, and NNTP servers.

Package: libgsf-1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 308
Maintainer: J.H.M. Dassen (Ray) <jdassen@debian.org>
Architecture: i386
Source: libgsf
Version: 1.12.3-3ubuntu3
Depends: libbz2-1.0, libc6 (>= 2.3.4-1), libglib2.0-0 (>= 2.8.0), libxml2 (>= 2.6.20), zlib1g (>= 1:1.2.1), gconf2 (>= 2.6.2-1), libgconf2-4
Conflicts: gnumeric (<< 1.4.4)
Description: Structured File Library - runtime version
 The GNOME Structured File Library library aims to provide an efficient
 extensible I/O abstraction for dealing with different structured file
 formats.
 .
 This is the basic runtime version of libgsf. It does not provide
 GNOME-specific extensions.

Package: konq-plugins
Status: install ok installed
Priority: optional
Section: kde
Installed-Size: 3588
Maintainer: Ben Burton <bab@debian.org>
Architecture: i386
Source: kdeaddons
Version: 4:3.5.1-0ubuntu0breezy1
Replaces: akregator (<< 1.1), akregator-konq-plugin (<< 1.1)
Provides: akregator-konq-plugin
Depends: kdelibs4c2 (>= 4:3.4.3-1), konqueror (>= 4:3.5-rc1-1), libacl1 (>= 2.2.11-1), libart-2.0-2 (>= 2.3.16), libarts1c2 (>= 1.4.3-1), libasound2 (>> 1.0.9), libattr1 (>= 2.4.4-1), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.4-1), libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0.1), libglib2.0-0 (>= 2.8.0), libice6, libidn11 (>= 0.5.13), libjpeg62, libkonq4 (>= 4:3.5-rc1-1), libogg0 (>= 1.1.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.8rel), libqt3-mt (>= 3:3.3.4), libsm6, libstdc++6 (>= 4.0.1), libvorbis0a (>= 1.1.0), libvorbisenc2 (>= 1.1.0), libvorbisfile3 (>= 1.1.0), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, zlib1g (>= 1:1.2.1), akregator, ark, imagemagick, libjpeg-progs, python
Suggests: khelpcenter, kdeaddons-doc-html
Conflicts: akregator-konq-plugin (<< 1.1)
Enhances: konqueror, akregator
Conffiles:
 /etc/kde3/translaterc 01166c8072d5fc205b30f880f0ca6200
Description: plugins for Konqueror, the KDE file/web/doc browser
 This package contains a variety of useful plugins for Konqueror, the
 file manager, web browser and document viewer for KDE.  Many of these
 plugins will appear in Konqueror's Tools menu.
 .
 Highlights for web browsing include web page translation, web page archiving,
 auto-refreshing, HTML and CSS structural analysis, a search toolbar, a
 sidebar news ticker, fast access to common options, bookmarklets, a crash
 monitor and integration with the aKregator RSS feed reader.
 .
 Highlights for directory browsing include directory filters, image gallery
 creation, archive compression and extraction, quick copy/move, a sidebar
 media player, a graphical disk usage viewer and image conversions and
 transformations.
 .
 This package is part of the KDE add-ons module.

Package: klibc-utils
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 280
Maintainer: Jeff Bailey <jbailey@ubuntu.com>
Architecture: i386
Source: klibc
Version: 1.0.14-1ubuntu4
Depends: libklibc (= 1.0.14-1ubuntu4)
Description: small statically-linked utilities built with klibc
 This package contains a collection of programs that are statically
 linked against klibc.  These duplicate some of the functionality of a
 regular Linux toolset, but are typically much smaller than their
 full-function counterparts.  They are intended for inclusion in
 initramfs images and embedded systems.

Package: xtrap
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 104
Maintainer: Fabio M. Di Nitto <fabbione@ubuntu.com>
Architecture: i386
Version: 0.99.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.3.4-1), libice6, libsm6, libx11-6, libxext6, libxt6, libxtrap6
Description: X client - xtrap
 xtrap is a small tool that was part of xbase-clients.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'app/xtrap' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

Package: krfb
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 1620
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdenetwork
Version: 4:3.5.1-0ubuntu0breezy1
Depends: kdelibs4c2 (>= 4:3.4.3-1), libart-2.0-2 (>= 2.3.16), libaudio2, libc6 (>= 2.3.4-1), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.1), libice6, libidn11 (>= 0.5.13), libjpeg62, libpng12-0 (>= 1.2.8rel), libqt3-mt (>= 3:3.3.4), libslp1, libsm6, libstdc++6 (>= 4.0.1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, libxtst6, zlib1g (>= 1:1.2.1)
Suggests: khelpcenter
Description: Desktop Sharing for KDE
 Desktop Sharing (krfb) is a server application that allows you to share
 your current session with a user on another machine, who can use a
 VNC client like krdc to view or even control the desktop. It doesn't
 require you to start a new X session - it can share the current session.
 This makes it very useful when you want someone to help you perform a
 task.
 .
 This package is part of KDE, as a component of the KDE network module.
 See the 'kde' and 'kdenetwork' packages for more information.

Package: openoffice.org2-java-common
Status: install ok installed
Priority: optional
Section: editors
Installed-Size: 3512
Maintainer: Debian OpenOffice Team <debian-openoffice@lists.debian.org>
Architecture: all
Source: openoffice.org2
Version: 1.9.129-0.1ubuntu4
Replaces: openoffice.org2-common (<= 1.9.127-0.1pre)
Depends: libxt-java, libxalan2-java (>= 2.6.0-1), libxerces2-java, bsh (>= 2.0b4-1)
Description: OpenOffice.org office suite Java support arch. independent files
 OpenOffice.org is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the architecture-independent files of
 the Java support for OpenOffice.org (Java classes, scripts, config snippets).
 See the openoffice.org2 package for more information.
 .
 For latest news on OpenOffice.org in Debian, see
 http://openoffice.debian.net

Package: python2.4-kjbuckets
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 144
Maintainer: Matthias Klose <doko@debian.org>
Architecture: i386
Source: gadfly (1.0.0-8ubuntu3)
Version: 1:1.0.0-8ubuntu3
Depends: python2.4, libc6 (>= 2.3.2.ds1-4)
Description: Set and graph data types for Python 2.4
 kjbuckets is a C extension to the Python interpreter which
 defines set and graph data types, as well as an alternative
 dictionary data type.  These types are tightly coupled at
 the level of C, allowing fast and powerful algebraic
 combinations of container objects.
 .
 This Debian package is built for Python 2.4.

Package: g++
Status: install ok installed
Priority: standard
Section: devel
Installed-Size: 40
Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: i386
Source: gcc-defaults (1.28)
Version: 4:4.0.1-3
Provides: c++-compiler
Depends: cpp (>= 4:4.0.1-3), gcc (>= 4:4.0.1-3), g++-4.0 (>= 4.0.1-2), gcc-4.0 (>= 4.0.1-2)
Description: The GNU C++ compiler
 This is the GNU C++ compiler, a fairly portable optimizing compiler for C++.
 .
 This is a dependency package providing the default GNU C++ compiler.

Package: e2fslibs
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 188
Maintainer: Theodore Y. Ts'o <tytso@mit.edu>
Architecture: i386
Source: e2fsprogs
Version: 1.38-2ubuntu1
Replaces: e2fsprogs (<< 1.34-1)
Provides: libext2fs2, libe2p2
Depends: libc6 (>= 2.3.4-1)
Description: ext2 filesystem libraries
 The ext2fs and e2p libraries are used by programs that directly access
 EXT2 filesystems from usermode programs.   The EXT2 filesystem is very often
 used as the default filesystem on Linux systems.   Various system programs
 that use libext2fs include e2fsck, mke2fs, tune2fs, etc.  Programs that use
 libe2p include dumpe2fs, chattr, and lsattr.

Package: libgnome-menu2
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 160
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: i386
Source: gnome-menus
Version: 2.12.0-0ubuntu2
Depends: libc6 (>= 2.3.4-1), libgamin0, libglib2.0-0 (>= 2.8.0)
Description: an implementation of the freedesktop menu specification for GNOME
 The package contains an implementation of the draft
 "Desktop Menu Specification" from freedesktop.org:
 .
 http://www.freedesktop.org/Standards/menu-spec
 .
 Also contained here are the GNOME menu layout configuration files, .directory
 files and assorted menu related utility programs.
 .
 This package contains the shared library.

Package: libeel2-2
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 684
Maintainer: Takuo KITAME <kitame@debian.org>
Architecture: i386
Source: eel2
Version: 2.12.1-0ubuntu1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.0), libfontconfig1 (>= 2.3.0), libgail-common (>= 1.6.6), libgail17 (>= 1.6.6), libgconf2-4 (>= 2.9), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.8.0), libgnome-desktop-2 (>= 2.9.91), libgnome-keyring0 (>= 0.4.3), libgnome-menu2, libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.11.3), libgtk2.0-0 (>= 2.8.0), libice6, liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.10.0), libpopt0 (>= 1.7), libsm6, libstartup-notification0 (>= 0.8-1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.20), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1), libeel2-data
Description: Eazel Extensions Library (for GNOME2)
 The Eazel Extensions Library is a collection of widgets and extensions
 to many modules of the GNOME platform.  These widgets and extensions
 were developed by hackers working on Nautilus.   For the duration of
 the Nautilus 1.0 development cycle, the code was internal to Nautilus
 and its components.
 .
 This package for GNOME2

Package: xfonts-scalable
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 720
Maintainer: Daniel Stone <daniels@debian.org>
Architecture: all
Source: xfonts-core
Version: 6.8.2.1-4
Depends: xfonts-utils
Pre-Depends: x-common (>= 1.0)
Suggests: xfs | xserver
Conffiles:
 /etc/X11/fonts/Type1/xfonts-scalable.scale 05a05d21e542d7f31e2ba9899c805e7a
Deed@EAGLE:~$         
```

---

### Post by arnieboy on 2006-03-09
well try this:
```
sudo gedit /var/lib/dpkg/available
```
when the file opens, take a close look at line 1 (first package listed) and make sure there are no blanks before the first letter. 
close the file and do a :
```
sudo apt-get update
```
let me know if this lists any errors.

---

### Post by R3linquish3r on 2006-03-10
I cant even open the file.....


```
gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.
```

---

### Post by R3linquish3r on 2006-03-10
bump

---

### Post by arnieboy on 2006-03-10
[QUOTE=R3linquish3r]bump[/QUOTE]
ok try moving the file:
```
sudo mv -f /var/lib/dpkg/available /var/lib/dpkg/available_backup
```
now do a 
```
sudo apt-get update
```
and now run synaptic

---

### Post by R3linquish3r on 2006-03-10
Still no good. After I moved it Synaptic wont downlaod and when I do apt-get (after doing apt-get update)  I get:

```
ed@EAGLE:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  cpp-3.4 evince gcc-3.4 gcc-3.4-base libgnome2-canvas-perl
  libnautilus-extension1 nautilus nautilus-data python-gnome2-extras
  python2.4-gnome2-extras
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7697kB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by arnieboy on 2006-03-10
try this:
```
sudo touch /var/lib/dpkg/available
```
now do
```
sudo apt-get update
```
then run synaptic

---

### Post by R3linquish3r on 2006-03-10
There we go! Thanks alot Arnie :)

---

### Post by arnieboy on 2006-03-10
glad to have been of help :)

---

