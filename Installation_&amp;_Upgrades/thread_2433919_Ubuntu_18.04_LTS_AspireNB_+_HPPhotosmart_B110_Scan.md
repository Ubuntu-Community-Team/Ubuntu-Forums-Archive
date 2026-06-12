---
title: "Ubuntu 18.04 LTS AspireNB + HPPhotosmart B110 Scanning V3.17.10-&gt;11 Upgrade"
date: 2019-12-27
forum: Installation &amp; Upgrades
---

### Post by donnywood-studio on 2019-12-27
Hello folks 

New Install  to Ubuntu 18.04LTS and trying to get HP Photosmart B110 wireless scanner function to work.

All function of the printer works except scanner ,ie Simple Scanner does not discover.  Checked and found this instruction below.It detected V3.17.10 in the base 18.04 LTS and asked  to uninstall and continue or abort, i chose to continue. Even under V3.17.10 scanning function could not be detected. 

Below some summary of the log during installation. 

Appreciate any pointer to get this scanning function going in 18.04 LTS. 

[ATTACH=CONFIG]284704[/ATTACH]

The following performed 
[LIST=1]
[*]Followed procedure under [https://websiteforstudents.com/installing-hp-printer-drivers-on-ubuntu-16-04-17-10-18-04-desktop/](https://websiteforstudents.com/installing-hp-printer-drivers-on-ubuntu-16-04-17-10-18-04-desktop/)
[*][B]ERROR During Verification 
[/B]**HP Linux Imaging and Printing System (ver. 3.17.11)**
**Self Diagnse Utility and Healing Utility ver. 1.0**

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


**HP Linux Imaging and Printing System (ver. 3.17.11)**
**Self Diagnse Utility and Healing Utility ver. 1.0**

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

|Gtk-[COLOR=#8AE234]**Message**[/COLOR]: [COLOR=#3465A4]12:00:39.756[/COLOR]: Failed to load module "canberra-gtk-module"
 

**Checking for Deprecated items....**
[COLOR=#EF2929]**error: This distro (i.e ubuntu  18.04) is either deprecated or not yet supported.**[/COLOR]
[COLOR=#EF2929]**The diagnosis is limited on unsupported platforms. Do you want to continue?(y=yes*, n=no):**[/COLOR]y


**Checking for HPLIP updates....**

**HP Linux Imaging and Printing System (ver. 3.17.11)**
**HPLIP upgrade latest version ver. 1.0**

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Latest version of HPLIP is already installed.


**Checking for Dependencies....**
[COLOR=#AD7FA8]**warning: 12-18.04 version is not supported. Using 12-17.10 versions dependencies to verify and install...**[/COLOR]

---------------
| SYSTEM INFO |
---------------

 Kernel: 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 GNU/Linux
 Host: wing-Aspire-V3-571G
 Proc: 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 GNU/Linux
 Distribution: 12 18.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.17.11
HPLIP-Home: /usr/share/hplip
[COLOR=#AD7FA8]**warning: HPLIP-Installation: Auto installation is not supported for 12 distro  18.04 version **[/COLOR]

**Current contents of '/etc/hp/hplip.conf' file:**
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.17.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.17.11
html=/usr/share/doc/hplip-3.17.11
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin
apparmor=/etc/apparmor.d
# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.17.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
qt5=no
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=yes
class-driver=no


**Current contents of '/var/lib/hp/hplip.state' file:**
Plugins are not installed. Could not access file: No such file or directory

**Current contents of '~/.hplip/hplip.conf' file:**
[upgrade]
notify_upgrade = true
last_upgraded_time = 1577485165
pending_upgrade_time = 0
latest_available_version = 3.17.10

[installation]
date_time = 12/28/19 12:00:40
version = 3.17.11


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

-------------------------
| External Dependencies |
-------------------------

 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.2.7           OK         'CUPS Scheduler is running'
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.26            OK         -
Gtk-[COLOR=#8AE234]**Message**[/COLOR]: [COLOR=#3465A4]12:00:53.505[/COLOR]: Failed to load module "canberra-gtk-module"
Gtk-[COLOR=#8AE234]**Message**[/COLOR]: [COLOR=#3465A4]12:00:53.524[/COLOR]: Failed to load module "canberra-gtk-module"
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.27          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.12.2          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 network              network -wget                                                OPTIONAL        -               1.19.4          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.7             OK         -

------------------------
| General Dependencies |
------------------------

 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.2.7           OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.2.7           OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.27'         OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.1.1           OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.6.9           OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 python3-pyqt4-dbus   PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             4.12.1          OK         -
 python3-pyqt4        PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.12.1          OK         -
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.6           OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.2.5           OK         -
 python3-devel        Python devel - Python development files                      REQUIRED        2.2             3.6.9           OK         -
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.4.0           OK         -

--------------
| COMPILEDEP |
--------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               7.4.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -

---------------------
| Python Extentions |
---------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.17.11         OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.17.11         OK         -

----------------------
| Scan Configuration |
----------------------

 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.17.11         OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.17.11         OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 

--------------
| PERMISSION |
--------------

 

**Checking for Configured Queues....**
 
[COLOR=#AD7FA8]**warning: No Queue(s) configured.**[/COLOR]


**Checking for HP Properitery Plugin's....**
No plug-in printers are configured.
 
**Diagnose completed...**



More information on Troubleshooting,How-To's and Support is available on [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)


Please close this terminal manually.
[/LIST]

---

### Post by donnywood-studio on 2019-12-28
Attach is  lshw.txt information of the hardware .  Also the OS is UBUNTU not LUBUNTU when posted . typo error

> **donnywood-studio said:**
> Hello folks 

New Install  to Ubuntu 18.04LTS and trying to get HP Photosmart B110 wireless scanner function to work.

All function of the printer works except scanner ,ie Simple Scanner does not discover.  Checked and found this instruction below.It detected V3.17.10 in the base 18.04 LTS and asked  to uninstall and continue or abort, i chose to continue. Even under V3.17.10 scanning function could not be detected. 

Below some summary of the log during installation. 

Appreciate any pointer to get this scanning function going in 18.04 LTS. 

[ATTACH=CONFIG]284704[/ATTACH]

The following performed 
[LIST=1]
[*]Followed procedure under [https://websiteforstudents.com/installing-hp-printer-drivers-on-ubuntu-16-04-17-10-18-04-desktop/](https://websiteforstudents.com/installing-hp-printer-drivers-on-ubuntu-16-04-17-10-18-04-desktop/)
[*][B]ERROR During Verification 
[/B]**HP Linux Imaging and Printing System (ver. 3.17.11)**
**Self Diagnse Utility and Healing Utility ver. 1.0**
[/LIST]


---

