---
title: "[SOLVED] HP LaserJet M1132 MFP Scanner Problem"
date: 2016-12-19
forum: MINT
---

### Post by aurelio-rei on 2016-12-19
Hello,

I need some help to get my scanner to work.
My multifunctional printer is an HP LaserJet M1132 MFP, i have already installed the latest version of HPLIP, and the printing works fine.
But the scanner won't work. I have tried several ways, searched in many forums but no procedure could solve the problem. Sorry for the bad english but I'll try to explain.
The error that always appears is: error: SANE: Error during device I/O (code=9), that message shows up if i try the command "hp-scan", for example. Xsane 0.999 won't work either, it will show me a similar message. Simple scan won't work either.
I use Linux Mint Cinnamon Sarah 18 - kernel 4.4.0-21-generic
The scanner is recognised by SANE - (result for sane-find-scanner: found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x042a [HP LaserJet Professional M1132 MFP]) at libusb:001:005)

I also have tried to insert the vendor and product directly in the hplip backend (/etc/sane.d/dll.d/hplip) but i don't that's the way to solve the issue.
Some information i'm finding useful but still can't figure out how to solve:

I'f i try "SANE_DEBUG_DLL=255 scanimage -L 2>&1 >&2 | tee /tmp/scanimage.out" it will give me the results:

```
[sanei_debug] Setting debug level of dll to 255.
[dll] sane_init: SANE dll backend version 1.0.13 from sane-backends 1.0.25git
[dll] sane_init/read_dlld: attempting to open directory `./dll.d'
[dll] sane_init/read_dlld: attempting to open directory `/etc/sane.d/dll.d'
[dll] sane_init/read_dlld: using config directory `/etc/sane.d/dll.d'
[dll] sane_init/read_dlld: considering /etc/sane.d/dll.d/hplip
[dll] sane_init/read_config: reading dll.d/hplip
[dll] add_backend: adding backend `hpaio'
[dll] add_backend: adding backend `usb'
[dll] sane_init/read_dlld: done.
[dll] sane_init/read_config: reading dll.conf
[dll] add_backend: adding backend `hp'
[dll] add_backend: adding backend `hpaio'
[dll] add_backend: `hpaio' is already there
[dll] add_backend: adding backend `“hpaio”'
[dll] sane_get_devices
[dll] load: searching backend `“hpaio”' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-“hpaio”.so.1'
[dll] load: couldn't open `/usr/lib/i386-linux-gnu/sane/libsane-“hpaio”.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-“hpaio”.so.1'
[dll] load: couldn't open `/usr/lib/sane/libsane-“hpaio”.so.1' (No such file or directory)
[dll] load: couldn't find backend `“hpaio”' (No such file or directory)
[dll] load: searching backend `hpaio' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hpaio.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hpaio.so.1'
[dll] init: initializing backend `hpaio'
[dll] init: backend `hpaio' is version 1.0.0
[dll] load: searching backend `hp' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hp.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hp.so.1'
[dll] init: initializing backend `hp'
[dll] init: backend `hp' is version 1.0.8
[dll] load: searching backend `usb' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-usb.so.1'
[dll] load: couldn't open `/usr/lib/i386-linux-gnu/sane/libsane-usb.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-usb.so.1'
[dll] load: couldn't open `/usr/lib/sane/libsane-usb.so.1' (No such file or directory)
[dll] load: couldn't find backend `usb' (No such file or directory)
[dll] sane_get_devices: found 1 devices
[dll] sane_exit: exiting
[dll] sane_exit: calling backend `hpaio's exit function
[dll] sane_exit: calling backend `hp's exit function
[dll] sane_exit: finished
device `hpaio:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000SS01NY0PR1a' is a Hewlett-Packard HP_LaserJet_Professional_M1132_MFP all-in-one
```

not sure if the problem relies here but it seems that the hpaio backend loads sucessfully, but the part "[dll] load: couldn't open `/usr/lib/i386-linux-gnu/sane/libsane-usb.so.1' (No such file or directory)" , got my attention, i really don't have that file , not even in /usr/lib/sane folder. 
also in /var/log/syslog, there's a few lines too that may be useful:

```
Dec 19 16:54:12 cobrancalaser-945GCM-S2C python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Dec 19 16:55:13 cobrancalaser-945GCM-S2C hp-scan: hp-scan[8759]: warning: No destinations specified. Adding 'file' destination by default.
Dec 19 16:55:13 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/pp.c 627: unable to read device-id ret=-1
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 427: Found interface conf=0, iface=0, altset=0, index=1
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 389: Active kernel driver on interface=0 ret=0
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 535: claimed 7/1/2 interface
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 780: read actual device_id successfully fd=1 len=150
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 561: released 7/1/2 interface
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 960: new HP-MARVELL-SCAN channel=21 clientCnt=1 channelCnt=1
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 427: Found interface conf=0, iface=2, altset=0, index=7
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 389: Active kernel driver on interface=2 ret=0
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 535: claimed ff/ff/ff interface
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 721: invalid channel_write state
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: bb_marvell.c 576: invalid set_default hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000SS01NY0PR1a
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 702: invalid channel_close state
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 569: invalid device_close state
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: hp-scan[8759]: error: SANE: Error during device I/O (code=9)
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 373: device_cleanup: device uri=hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000SS01NY0PR1a
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 379: device_cleanup: close channel 21...
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 561: released ff/ff/ff interface
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/musb.c 975: removed HP-MARVELL-SCAN channel=21 clientCnt=0 channelCnt=0
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 381: device_cleanup: done closing channel 21
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 385: device_cleanup: close device dd=1...
Dec 19 16:56:15 cobrancalaser-945GCM-S2C hp-scan: io/hpmud/hpmud.c 387: device_cleanup: done closing device dd=1
```

and finally the results for hp-check -t

Saving output in log file: /home/cobrancalaser/hp-check.log

```
HP Linux Imaging and Printing System (ver. 3.16.11)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Check types:                                                                    
a. EXTERNALDEP - External Dependencies                                          
b. GENERALDEP - General Dependencies (required both at compile and run time)    
c. COMPILEDEP - Compile time Dependencies                                       
d. [All are run-time checks]                                                    
PYEXT SCANCONF QUEUES PERMISSION                                                

Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version

 
---------------
| SYSTEM INFO |
---------------

 Kernel: 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:34:49 UTC 2016 GNU/Linux
 Host: cobrancalaser-945GCM-S2C
 Proc: 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:34:49 UTC 2016 GNU/Linux
 Distribution: 22 18
 Bitness: 32 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.16.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for linuxmint distro  18 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.16.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.16.11
html=/usr/share/doc/hplip-3.16.11
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
internal-tag=3.16.11
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


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.16.11



Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = false
last_upgraded_time = 1481893556
pending_upgrade_time = 0
latest_available_version = 3.16.11

[last_used]
device_uri = hpaio:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000SS01NY0PR1a
printer_name = 
working_dir = .

[settings]
systray_visible = 0
systray_messages = 0

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
interval = 5
device_list = 

[fax]
voice_phone = 
email_address = 

[installation]
date_time = 19/12/2016 18:06:21
version = 3.16.11


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------
| COMPILEDEP |
--------------

 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               5.4.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -

------------------------
| General Dependencies |
------------------------

 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.1.0           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               1.0.25          OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.11.4          OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.23            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.12          OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.1.3           OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.0           OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.3.0           OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.1.3           OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.12          OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               1.0.25          OK         -

----------------------
| Scan Configuration |
----------------------

 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.16.11         OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.16.11         OK         'hpaio found in /etc/sane.d/dll.conf'

-------------------------
| External Dependencies |
-------------------------

 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.18            OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.17.1          OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.6          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -

---------------------
| Python Extentions |
---------------------

 hpmudext             IO-Extension                                                 REQUIRED        -               3.16.11         OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.16.11         OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000SS01NY0PR1a' is a Hewlett-Packard HP_LaserJet_Professional_M1132_MFP all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                           
  --------------------------------  --------------------------------
  hp:/usb/HP_LaserJet_Professional  HP LaserJet Professional M1132  
  _M1132_MFP?serial=000000000SS01N  MFP                             
  Y0PR1a                                                            

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Argox-Driver
------------
Type: Unknown
Device URI: ipps://ricardo-desktop.local:631/printers/Argox-Driver

HP-P1102w-Caixa-Ha
------------------
Type: Unknown
Device URI: ipps://reihau5.local:631/printers/HP-P1102w-Caixa-Ha

HP_LaserJet_M1132_MFP_Cobranca
------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000SS01NY0PR1a
PPD: /etc/cups/ppd/HP_LaserJet_M1132_MFP_Cobranca.ppd
warning: Failed to read /etc/cups/ppd/HP_LaserJet_M1132_MFP_Cobranca.ppd ppd file
PPD Description: 
Printer status: printer HP_LaserJet_M1132_MFP_Cobranca is idle.  enabled since Seg 19 Deready to print5 BRST
Required plug-in status: Installed
Communication status: Good

HP_LaserJet_Professional_M1132_MFP
----------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000SS01NY0PR1a
PPD: /etc/cups/ppd/HP_LaserJet_Professional_M1132_MFP.ppd
warning: Failed to read /etc/cups/ppd/HP_LaserJet_Professional_M1132_MFP.ppd ppd file
PPD Description: 
Printer status: printer HP_LaserJet_Professional_M1132_MFP is idle.  enabled since Sex 16 Dez 2016 11:16:33 BRST
Required plug-in status: Installed
Communication status: Good

LaserLonas
----------
Type: Unknown
Device URI: implicitclass:LaserLonas


--------------
| PERMISSION |
--------------

USB             HP_LaserJet_M1132_MFP_Cobranca Required        -        -        OK       Node:'/dev/bus/usb/001/005' Perm:'  root  lp rw- rw- rw- rw- r--'
No errors or warnings.
```

Done.

So if anyone could help me solve that issue i would apreciate.
Thanks

Aurélio

---

### Post by howefield on 2016-12-19
Thread moved to the "*MINT*" forum and tidied up to [conform]("https://ubuntuforums.org/showthread.php?t=2158945").

---

### Post by #&amp;thj^% on 2016-12-19
HPLIP software is not used in support of scanning on certain multifunction products (MFP's), some of which are listed below.  These products which use HP Digital Sending Technology allow scanning directly to email addresses, network folders, or other networked devices.

[http://hplipopensource.com/node/302](http://hplipopensource.com/node/302)

But here is an older guide that might still work:
[http://www.andersaaberg.dk/2012/scanning-with-hp-laserjet-m1132-mfp-for-ubuntu-12-04/](http://www.andersaaberg.dk/2012/scanning-with-hp-laserjet-m1132-mfp-for-ubuntu-12-04/)

Good luck

---

### Post by martin154 on 2016-12-20
hi,

i recently reinstalled mint version 18.1 mate. I have a brother printer/scanner and I got the printing working ok, but was stumbling on the scanner. In the end I found instructions online where I had to make a lib64 folder and copy the sane 32 files there. Maybe it is a similar problem?  Here is the instruction I had to follow, look at the end for the copying instruction. 

[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

regards
Martin

---

### Post by aurelio-rei on 2016-12-20
Thank you for your reply, but still couldn't do it.

According to  the table at  [http://hplipopensource.com/hplip-web/supported_devices/laserjet.html](http://hplipopensource.com/hplip-web/supported_devices/laserjet.html),  the match for "Scan to PC" for my printer is "Yes", while printers that  use Digital Sending matches "DS". Seems LaserJet M1132 MFP do not use  that technology.

And trying that guide you pointed me at [http://www.andersaaberg.dk/2012/scan...-ubuntu-12-04/]("http://www.andersaaberg.dk/2012/scanning-with-hp-laserjet-m1132-mfp-for-ubuntu-12-04/"),  well, the first thing he does is entering the command "hp-scan" in the  terminal, and as i said, when i try that command i get  [COLOR=#ff0000]error: SANE: Error during device I/O (code=9)


[/COLOR][COLOR=#000000]Andabou[/COLOR][COLOR=#000000]t the lib64, i don't think is quite the same problem, because my system is 32bit. But maybe it has something to do with libsane, in my case, as posted above, the log points that hplip can't find the backend "usb" with "libsane-usb.so.1". In your case you had the backend in another folder. But in my case i don't know if i have such backend[/COLOR][COLOR=#ff0000]
[/COLOR]

---

### Post by aurelio-rei on 2016-12-21
Solved my problem.

I've installed the printer in Ubuntu 16.04. Printer and scanner worked.

Thank you.

---

