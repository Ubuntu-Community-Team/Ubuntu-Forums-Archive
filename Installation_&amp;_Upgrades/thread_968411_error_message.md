---
title: "error message"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by skierfrmct on 2008-11-02
I am a linux noob and am slowly working up my knowledge...this though i can not figure out..i am trying to set up my new hp photosmart c4580 printer..i know that it isn't currently hplip supported but i am hoping to get it going until it gets listed....below is the error message i keep receiving when i try to follow some of the info i have taken from other threadz...
please advise...

o@dell-desktop:~$ hp-setup

HP Linux Imaging and Printing System (ver. 2.8.2)
Printer/Fax Setup Utility ver. 7.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: You must be root to run this utility.

below is the complete hp-check i ran...again i don't really know what i am doing here and not much has been dug up on this particular wireless printer,copier,scanner
it does print with no problems when i have it connected to my usb port.
thank you for any help..i know this is probably much longer than needed but i just wanted to offer as much info as i have.

Saving output in log file: hp-check.log

Initializing. Please wait...
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux dell-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
error: Yes, HPOJ is running. HPLIP is not compatible with HPOJ. To run HPLIP, please remove HPOJ.

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.7


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

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: python-devel - Python development files...
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
HPLIP 2.8.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.2.10


-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Tue 22 Apr 2008 05:56:20 PM EDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
Photosmart_C4500_series
-----------------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Photosmart_C4500_series?serial=CN88JF10MK057K
PPD: /etc/cups/ppd/Photosmart_C4500_series.ppd
PPD Description: HP PhotoSmart C4380 Foomatic/hpijs, hpijs 2.8.2
Printer status: printer Photosmart_C4500_series is idle.  enabled since Sun 02 Nov 2008 05:49:19 PM EST
error: Unsupported model: Photosmart_C4500_series


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname Laptop Integrated Webcam virtual device


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
 
HP Device 0x6b11 at 007:003: 
    Device URI: hp:/usb/Photosmart_C4500_series?serial=CN88JF10MK057K
    Device node: /dev/bus/usb/007/003
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/007/003
# owner: lp
# group: scanner
user::rw-
user:benito:rw-
group::rw-
mask::rw-
other::---



-----------
| SUMMARY |
-----------

error: 5 errors and/or warnings.

---

### Post by Partyboi2 on 2008-11-02
Here are some of the answers
>  error: You must be root to run this utility.Use ```
sudo hp-setup
```> HPOJ running?
error: Yes, HPOJ is running. HPLIP is not compatible with HPOJ. To run HPLIP, please remove HPOJ remove HPOJ
```
sudo apt-get remove hpoj
```> 'hpaio' in '/etc/sane.d/dll.conf'...
error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).

 Add hpaio to /etc/sane.d/dll.conf
```
sudo nano /etc/sane.d/dll.conf
``` at the bottom add
```
hpaio
``` then
```
ctrl+o
enter
Ctrl+x
```
Then run
```
sudo hp-setup
```

---

### Post by skierfrmct on 2008-11-05
thank you for taking the time to read through my code and straighten me out partyboi2!!

---

