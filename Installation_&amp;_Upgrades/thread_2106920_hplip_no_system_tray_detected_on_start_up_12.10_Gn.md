---
title: "hplip no system tray detected on start up 12.10 Gnome Classic"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by rufenach on 2013-01-20
I recently purchased hp m1212 all-in-one, after an installation it is not printing, that is the hp-setup will not detect the usb or in command line the following message "no device found on bus:usb" even though my previous Hp printer p1006 installs and setup correctly and prints fine. I suspect that at least part of the problem is that on start up, the following error is given: HPLIP Status Service: "no system tray detected in this system Unable to start, existing". I am not an experienced user, so if the fix requires that text in the start up menu be changed, then I will not detailed information about what file to modify, etc. I have tried using the command line "hp-systray" in both root and Desktop which countains hplip (see [http://linuxforums.org.uk/index.php?topic=10323.0](http://linuxforums.org.uk/index.php?topic=10323.0)) with the following result:

cliff@cliff-HP-Pavilion-dm4-Notebook-PC:~$ cd Desktop
cliff@cliff-HP-Pavilion-dm4-Notebook-PC:~/Desktop$ [http://linuxforums.org.uk/index.php?topic=10323.0](http://linuxforums.org.uk/index.php?topic=10323.0)
bash: [http://linuxforums.org.uk/index.php?topic=10323.0:](http://linuxforums.org.uk/index.php?topic=10323.0:) No such file or directory
cliff@cliff-HP-Pavilion-dm4-Notebook-PC:~/Desktop$ 

The command line  hp-check -b gives the following error in red:

error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ61XQ1SI1c
error: Device not found
error: Communication status: Failed

HP_LaserJet_Professional_M1212nf_MFP_fax
----------------------------------------
Type: Fax
Device URI: hpfax:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ61XQ1SI1c
PPD: /etc/cups/ppd/HP_LaserJet_Professional_M1212nf_MFP_fax.ppd
PPD Description: HP Fax3 hpcups
Printer status: printer HP_LaserJet_Professional_M1212nf_MFP_fax is idle.  enabled since Sat 19 Jan 2013 07:26:23 PM MST
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hpfax:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ61XQ1SI1c
error: Device not found
error: Communication status: Failed

The full output from the command line  hp-check -b is:


cliff@cliff-HP-Pavilion-dm4-Notebook-PC:~/Desktop$ hp-check -b

HP Linux Imaging and Printing System (ver. 3.12.11)
Dependency/Version Check Utility ver. 15

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
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

Saving output in log file: /home/cliff/Desktop/hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

 Kernel: 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 GNU/Linux
 Host: cliff-HP-Pavilion-dm4-Notebook-PC
 Proc: 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 GNU/Linux
 Distribution: ubuntu 12.10

-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.12.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  12.10 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.11
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

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
internal-tag=3.12.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.12.11



Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = false
last_upgraded_time = 1358688851
pending_upgrade_time = 0
latest_available_version = 3.12.11

[scan_plugins]
bb_marvell.so = Present
bb_soapht.so = Present
bb_soap.so = Present

[fax_plugins]
fax_marvell.so = Present

[print_plugins]
lj.so = Present

[installation]
date_time = 01/20/2013 10:47:52
version = 3.12.11


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 gs                   Ghostscript               REQUIRED        7.05            9.06            OK         -
 network              Network-wget              OPTIONAL        -               1.13.4          OK         -
 dbus                 DBus                      REQUIRED        -               1.6.4           OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 policykit            Admin-Policy-framework    OPTIONAL        -               0.104           OK         -
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -
 cups                 CUPS                      REQUIRED        1.1             1.6.1           OK         'CUPS Scheduler is running'

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.5             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.9.3           OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.15            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.1.1           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.3           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.9.3           OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.6.1           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.6.1           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.4.3           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 gcc                  gcc-Compiler              REQUIRED        -               4.7.2           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.12.11         OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.12.11         OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.12.11         OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.12.11         OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.12.11         OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model            
  --------------------------------  -----------------
  hp:/usb/HP_LaserJet_P1006?serial  HP LaserJet P1006
  =AC29J7D                                           

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_P1006
-----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_P1006?serial=AC29J7D
PPD: /etc/cups/ppd/HP_LaserJet_P1006.ppd
PPD Description: HP LaserJet p1006, hpcups 3.12.11, requires proprietary plugin
Printer status: printer HP_LaserJet_P1006 is idle.  enabled since Sun 20 Jan 2013 08:16:42 AM MST
Required plug-in status: Installed
Communication status: Good

HP_LaserJet_Professional_M1212nf_MFP
------------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ61XQ1SI1c
PPD: /etc/cups/ppd/HP_LaserJet_Professional_M1212nf_MFP.ppd
PPD Description: HP LaserJet Professional m1212nf MFP, hpcups 3.12.11, requires proprietary plugin
Printer status: printer HP_LaserJet_Professional_M1212nf_MFP is idle.  enabled since Sat 19 Jan 2013 07:26:23 PM MST
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ61XQ1SI1c
error: Device not found
error: Communication status: Failed

HP_LaserJet_Professional_M1212nf_MFP_fax
----------------------------------------
Type: Fax
Device URI: hpfax:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ61XQ1SI1c
PPD: /etc/cups/ppd/HP_LaserJet_Professional_M1212nf_MFP_fax.ppd
PPD Description: HP Fax3 hpcups
Printer status: printer HP_LaserJet_Professional_M1212nf_MFP_fax is idle.  enabled since Sat 19 Jan 2013 07:26:23 PM MST
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hpfax:/usb/HP_LaserJet_Professional_M1212nf_MFP?serial=000000000QJ61XQ1SI1c
error: Device not found
error: Communication status: Failed


--------------
| PERMISSION |
--------------

groups          user-groups                    Required        -        -        OK       cliff adm lp cdrom sudo dip plugdev lpadmin sambashare

USB             HP_LaserJet_P1006              Required        -        -        OK       Node:'/dev/bus/usb/003/003' Perm:'  root  lp rw- rw- rw- rw- r--'

-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
None

Missing Optional Dependencies
-----------------------------
None


Total Errors: 2
Total Warnings: 0


Done.
cliff@cliff-HP-Pavilion-dm4-Notebook-PC:~/Desktop$

---

### Post by thomassisson on 2013-04-01
This is a me too reply. I'm sorry to do this the wrong way, but there is no "I have this problem" mechanism available. Also, I wish to keep this thread alive in hopes that someone will post an answer. I will post an answer, if I remember, if I find one.

---

### Post by MyR on 2013-04-02
open up the "startup applications" editor from the admin menu.

add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

Also I'd recommend giving Linux Mint a try if you like classic gnome. The MATE desktop is based on gnome2.

peace

---

