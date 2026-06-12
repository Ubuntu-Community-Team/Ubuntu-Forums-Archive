---
title: "Unable to scan with HP PSC 1210 and XSANE"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by tpwgp38 on 2008-11-24
I've had the same problem on ubuntu 8.4 and 8.10, I've followed every piece of advice I could find.  

I installed hplip. 
I ran hp-check and have no errors or warnings. 
I have made sure user has permission to use scanners. 
Whenver I launch XSANE Image Scanner, I get the error message: 

Failed to open device hpaio:/usb/psc_1200_series?serial=MY3B4FB3PKSH'; Error during device I/O. 

I noticed the following entries in the system log which correspond to launching XSANE:

Nov 24 21:13:21 ted-desktop xsane: io/hpmud/mlc.c 179: unable to read MlcReverseCmd header: Resource temporarily unavailable
Nov 24 21:13:22 ted-desktop xsane: io/hpmud/musb.c 1629: invalid MlcCredit from peripheral, trying miser
Nov 24 21:14:06 ted-desktop xsane: io/hpmud/mlc.c 179: unable to read MlcReverseCmd header: Resource temporarily unavailable
Nov 24 21:14:06 ted-desktop xsane: io/hpmud/musb.c 1634: invalid MlcCredit from peripheral
Nov 24 21:15:46 ted-desktop xsane: io/hpmud/hpmud.c 323: device_cleanup: device uri=hp:/usb/psc_1200_series?serial=MY3B4FB3PK5H
Nov 24 21:15:46 ted-desktop xsane: io/hpmud/hpmud.c 335: device_cleanup: close device dd=1...
Nov 24 21:15:46 ted-desktop xsane: io/hpmud/hpmud.c 337: device_cleanup: done closing device dd=1
Nov 24 21:17:01 ted-desktop /USR/SBIN/CRON[6384]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Nov 24 21:19:18 ted-desktop kernel: [ 1873.582503] ppdev0: registered pardevice
Nov 24 21:19:18 ted-desktop kernel: [ 1873.583480] ppdev0: unregistered pardevice
Nov 24 21:20:01 ted-desktop /USR/SBIN/CRON[6617]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov 24 21:20:04 ted-desktop xsane: io/hpmud/mlc.c 179: unable to read MlcReverseCmd header: Resource temporarily unavailable
Nov 24 21:20:04 ted-desktop xsane: io/hpmud/musb.c 1629: invalid MlcCredit from peripheral, trying miser
Nov 24 21:20:49 ted-desktop xsane: io/hpmud/mlc.c 179: unable to read MlcReverseCmd header: Resource temporarily unavailable
Nov 24 21:20:49 ted-desktop xsane: io/hpmud/musb.c 1634: invalid MlcCredit from peripheral

---

### Post by tpwgp38 on 2008-11-24
ted@ted-desktop:~$ hp-check

HP Linux Imaging and Printing System (ver. 2.8.10)
Dependency/Version Check Utility ver. 14.1

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
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

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux ted-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.10

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt 3.x version...
OK, version 3.17 installed.

Checking PyQt 4.x version...

Checking for CUPS...
Status: scheduler is running
Version: 1.3.9
error_log is set to level: warn
note: For troubleshooting printing issues, it is best to have the CUPS 'LogLevel'
note: set to 'debug'. To set the LogLevel to debug, edit the file /etc/cups/cupsd.conf (as root),
note: and change the line near the top of the file that begins with 'LogLevel' to read:
note: LogLevel debug
note: Save the file and then restart CUPS (see your OS/distro docs on how to restart CUPS).
note: Now, when you print, helpful debug information will be saved to the file:
note: /var/log/cups/error_log
note: You can monitor this file by running this command in a console/shell:
note: tail -f /var/log/cups/error_log

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.82.4


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: dbus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 3- Qt interface for Python (for Qt version 3.x)...
OK, found.

Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
OK, found.

Checking for dependency: python-ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: python-dbus - Python bindings for dbus...
OK, found.

Checking for dependency: python-devel - Python development files...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.10 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=2.8.10

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-2.8.10
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=yes
internal-tag=2.8.10.33
restricted-build=no
ui-toolkit=qt3



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
device_uri = hp:/usb/psc_1200_series?serial=MY3B4FB3PK5H

[installation]
version = 2.8.10.33
date_time = 11/24/08 21:43:02



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model             
  --------------------------------  ------------------
  hp:/usb/psc_1200_series?serial=M  HP psc 1200 series
  Y3B4FB3PK5H                                         

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
psc_1200
--------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/psc_1200_series?serial=MY3B4FB3PK5H
PPD: /etc/cups/ppd/psc_1200.ppd
PPD Description: HP PSC 1200 series Foomatic/hpijs, hpijs 2.8.10
Printer status: printer psc_1200 is idle.  enabled since Mon 24 Nov 2008 07:15:18 PM EST
Communication status: Good

psc_1200_2
----------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/psc_1200_series?serial=MY3B4FB3PK5H
PPD: /etc/cups/ppd/psc_1200_2.ppd



PPD Description: HP PSC 1200 series Foomatic/hpijs, hpijs 2.8.7
Printer status: printer psc_1200_2 is idle.  enabled since Mon 24 Nov 2008 08:41:04 PM EST
Communication status: Good

psc_1200_series
---------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/psc_1200_series?serial=MY3B4FB3PK5H
PPD: /etc/cups/ppd/psc_1200_series.ppd
PPD Description: HP PSC 1200 Foomatic/hpijs, hpijs 2.8.2
Printer status: printer psc_1200_series is idle.  enabled since Mon 24 Nov 2008 07:15:18 PM EST
Communication status: Good

psc_1210
--------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/psc_1200_series?serial=MY3B4FB3PK5H
PPD: /etc/cups/ppd/psc_1210.ppd
PPD Description: HP PSC 1200 series Foomatic/hpijs, hpijs 2.8.10
Printer status: printer psc_1210 is idle.  enabled since Mon 24 Nov 2008 07:15:19 PM EST
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/psc_1200_series?serial=MY3B4FB3PK5H' is a Hewlett-Packard psc_1200_series all-in-one


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
HP Device 0x2f11 at 003:002: 
    Device URI: hp:/usb/psc_1200_series?serial=MY3B4FB3PK5H
    Device node: /dev/bus/usb/003/002
    Mode: 0666
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/003/002
# owner: root
# group: lp
user::rw-
user:ted:rw-
group::rw-
mask::rw-
other::rw-



-----------
| SUMMARY |
-----------

No errors or warnings.

Done.
ted@ted-desktop:~$

---

### Post by priegog on 2009-04-11
Have you solved this? I assume you have jaunty installed... Let me know if you need help...

---

### Post by pvfjr on 2009-07-21
I've got the same issue.  It prints fine, but can't scan.  Any ideas?

---

### Post by jakupl on 2009-09-30
I have the same problem... this needs to be resolved.

---

### Post by hbbliss on 2009-10-16
Note that in the hp-check (look carefully) there is a line in the ... determined at compile time and cannot be changed that says pp-build=no. To overcome this do a manual install (see the web site instructions).Be sure to use the sliders to ensure that you get the whole command line. At the configure command line add --enable-pp-build before executing. Assuming a successful compile and install running hp-setup will give you a chance to specify parallel port. Unfortunately, Xsane treats parallel scanners as belonging to root. Try sudo xane and see if your scanner is there. Hope this helps.

---

### Post by pvfjr on 2009-10-19
Well this thing is USB, so I'm not sure about this parallel port business.  Also, I have no clue how to compile and all that, so I guess I'm screwed for now.

---

