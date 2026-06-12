---
title: "Cups completely messed up"
date: 2018-10-15
forum: Installation &amp; Upgrades
---

### Post by angelo16 on 2018-10-15
Hi guys, after upgrade hplip I did messed with cups in my system. I deleted cups dir and now I cannot print anything

I need to know how to perform full clean cups install.

I already did 
sudo apt-get update
sudo apt-get install cups

however when I go to 127.0.0.1:631  I had the following message:
This site can&#8217;t be reached

127.0.0.1 refused to connect.


It seems that daemon is not running.

which is strange, as the install should take care to start the daemon.

---

### Post by angelo16 on 2018-10-16
Ok, found very similar post !! 60% solved....

I did the partial fix found in 
[https://ubuntuforums.org/showthread.php?t=2402609&highlight=cups](https://ubuntuforums.org/showthread.php?t=2402609&highlight=cups)

sudo cp /usr/share/cups/cupsd.conf.default /etc/cups/cupsd.conf

sudo systemctl restart [COLOR=#417394]cups[/COLOR]

---

### Post by angelo16 on 2018-10-16
Then this:

[https://ubuntuforums.org/showthread.php?t=2388741](https://ubuntuforums.org/showthread.php?t=2388741)

finishing with a cups restart

[COLOR=#000000]sudo systemctl restart [/COLOR][COLOR=#417394]cups


[/COLOR][COLOR=#000000]but I still unable to print with filter fail error.

[/COLOR]

---

### Post by angelo16 on 2018-10-16
this is what I have in /var/log/cups/error_log




```
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseOrder on line 7 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseAllow on line 8 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown Location directive Port on line 17 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseOrder on line 7 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseAllow on line 8 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown Location directive Port on line 17 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseOrder on line 7 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseAllow on line 8 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown Location directive Port on line 17 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseOrder on line 7 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseAllow on line 8 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown Location directive Port on line 17 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseOrder on line 7 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown directive BrowseAllow on line 8 of /etc/cups/cupsd.conf.
E [16/Oct/2018:00:05:15 -0300] Unknown Location directive Port on line 17 of /etc/cups/cupsd.conf.
E [16/Oct/2018:07:19:33 -0300] [cups-deviced] PID 13121 (gutenprint52+usb) stopped with status 1!
W [16/Oct/2018:07:20:14 -0300] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'HP_LaserJet_1022-Gray..\' already exists
E [16/Oct/2018:07:20:55 -0300] [Job 58] Job stopped due to filter errors; please consult the error_log file for details.
D [16/Oct/2018:07:20:55 -0300] [Job 58] The following messages were recorded from 07:20:30 to 07:20:55
D [16/Oct/2018:07:20:55 -0300] [Job 58] Applying default options...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Adding start banner page "none".
D [16/Oct/2018:07:20:55 -0300] [Job 58] Adding end banner page "none".
D [16/Oct/2018:07:20:55 -0300] [Job 58] File of type application/vnd.cups-pdf-banner queued by "anonymous".
D [16/Oct/2018:07:20:55 -0300] [Job 58] hold_until=0
D [16/Oct/2018:07:20:55 -0300] [Job 58] Queued on "HP_LaserJet_1022" by "anonymous".
D [16/Oct/2018:07:20:55 -0300] [Job 58] time-at-processing=1539685230
D [16/Oct/2018:07:20:55 -0300] [Job 58] 3 filters for job:
D [16/Oct/2018:07:20:55 -0300] [Job 58] bannertopdf (application/vnd.cups-pdf-banner to application/pdf, cost 32)
D [16/Oct/2018:07:20:55 -0300] [Job 58] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [16/Oct/2018:07:20:55 -0300] [Job 58] foomatic-rip (application/vnd.cups-pdf to printer/HP_LaserJet_1022, cost 0)
D [16/Oct/2018:07:20:55 -0300] [Job 58] job-sheets=none,none
D [16/Oct/2018:07:20:55 -0300] [Job 58] argv[0]="HP_LaserJet_1022"
D [16/Oct/2018:07:20:55 -0300] [Job 58] argv[1]="58"
D [16/Oct/2018:07:20:55 -0300] [Job 58] argv[2]="anonymous"
D [16/Oct/2018:07:20:55 -0300] [Job 58] argv[3]="Test Page"
D [16/Oct/2018:07:20:55 -0300] [Job 58] argv[4]="1"
D [16/Oct/2018:07:20:55 -0300] [Job 58] argv[5]="job-uuid=urn:uuid:f60a3de5-4428-3856-5991-fbc69dc4bbad job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1539685230 time-at-processing=1539685230"
D [16/Oct/2018:07:20:55 -0300] [Job 58] argv[6]="/var/spool/cups/d00058-001"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[7]="CUPS_STATEDIR=/run/cups"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[8]="HOME=/var/spool/cups/tmp"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[10]="SERVER_ADMIN=root@Angelo-451"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[11]="SOFTWARE=CUPS/2.2.7"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[13]="USER=root"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[14]="CUPS_MAX_MESSAGE=2047"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[15]="CUPS_SERVER=/run/cups/cups.sock"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[17]="IPP_PORT=631"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[18]="CHARSET=utf-8"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[19]="LANG=en_IE.UTF-8"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[20]="PPD=/etc/cups/ppd/HP_LaserJet_1022.ppd"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[21]="RIP_MAX_CACHE=128m"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[23]="DEVICE_URI=usb://HP/LaserJet%201022?serial=J500189"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[24]="PRINTER_INFO=HP LaserJet 1022"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[25]="PRINTER_LOCATION="
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[26]="PRINTER=HP_LaserJet_1022"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[27]="PRINTER_STATE_REASONS=none"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[28]="CUPS_FILETYPE=document"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-pdf"
D [16/Oct/2018:07:20:55 -0300] [Job 58] envp[30]="AUTH_I****"
D [16/Oct/2018:07:20:55 -0300] [Job 58] Started filter /usr/lib/cups/filter/bannertopdf (PID 13188)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Started filter /usr/lib/cups/filter/pdftopdf (PID 13189)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Started filter /usr/lib/cups/filter/foomatic-rip (PID 13190)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Started backend /usr/lib/cups/backend/usb (PID 13191)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Loading USB quirks from \"/usr/share/cups/usb\".
D [16/Oct/2018:07:20:55 -0300] [Job 58] Loaded 159 quirks.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Printing on printer with URI: usb://HP/LaserJet%201022?serial=J500189
D [16/Oct/2018:07:20:55 -0300] [Job 58] libusb_get_device_list=14
D [16/Oct/2018:07:20:55 -0300] [Job 58] STATE: +connecting-to-device
D [16/Oct/2018:07:20:55 -0300] [Job 58] STATE: -connecting-to-device
D [16/Oct/2018:07:20:55 -0300] [Job 58] Printer found with device ID: MFG:Hewlett-Packard;MDL:HP LaserJet 1022;CMD:ACL;CLS:PRINTER;DES:HP LaserJet 1022;FWVER:20050401; Device URI: usb://HP/LaserJet%201022?serial=J500189
D [16/Oct/2018:07:20:55 -0300] [Job 58] Device protocol: 2
D [16/Oct/2018:07:20:55 -0300] [Job 58] Sending data to printer.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [16/Oct/2018:07:20:55 -0300] [Job 58] PDF template file doesn\'t have form. It\'s okay.
D [16/Oct/2018:07:20:55 -0300] [Job 58] PID 13188 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [16/Oct/2018:07:20:55 -0300] [Job 58] pdftopdf: Last filter determined by the PPD: foomatic-rip; FINAL_CONTENT_TYPE: application/vnd.cups-pdf => pdftopdf will log pages in page_log.
D [16/Oct/2018:07:20:55 -0300] [Job 58] PAGE: 1 1
D [16/Oct/2018:07:20:55 -0300] [Job 58] PID 13189 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Calling FindDeviceById(cups-HP_LaserJet_1022)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found device /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_1022
D [16/Oct/2018:07:20:55 -0300] [Job 58] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [16/Oct/2018:07:20:55 -0300] [Job 58] \'CM Color Calibration\' Mode in SPOOLER-LESS: Off
D [16/Oct/2018:07:20:55 -0300] [Job 58] Getting input from file 
D [16/Oct/2018:07:20:55 -0300] [Job 58] foomatic-rip version 1.20.2 running...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Parsing PPD file ...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option ColorSpace
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option PageSize
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option Quality
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option Resolution
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option ImageableArea
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option PaperDimension
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option InputSlot
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option MediaType
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option Density
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option Copies
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option halftone
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option NupOrient
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option NupPages
D [16/Oct/2018:07:20:55 -0300] [Job 58] Added option Font
D [16/Oct/2018:07:20:55 -0300] [Job 58] Parameter Summary
D [16/Oct/2018:07:20:55 -0300] [Job 58] -----------------
D [16/Oct/2018:07:20:55 -0300] [Job 58] Spooler: cups
D [16/Oct/2018:07:20:55 -0300] [Job 58] Printer: HP_LaserJet_1022
D [16/Oct/2018:07:20:55 -0300] [Job 58] Shell: /bin/sh
D [16/Oct/2018:07:20:55 -0300] [Job 58] PPD file: /etc/cups/ppd/HP_LaserJet_1022.ppd
D [16/Oct/2018:07:20:55 -0300] [Job 58] ATTR file: 
D [16/Oct/2018:07:20:55 -0300] [Job 58] Printer model: HP LaserJet 1022 Foomatic/foo2zjs-z1 (recommended)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Job title: Test Page
D [16/Oct/2018:07:20:55 -0300] [Job 58] File(s) to be printed:
D [16/Oct/2018:07:20:55 -0300] [Job 58] <STDIN>
D [16/Oct/2018:07:20:55 -0300] [Job 58] Ghostscript extra search path (\'GS_LIB\'): /usr/share/cups/fonts
D [16/Oct/2018:07:20:55 -0300] [Job 58] Printing system options:
D [16/Oct/2018:07:20:55 -0300] [Job 58] Pondering option \'job-uuid=urn:uuid:f60a3de5-4428-3856-5991-fbc69dc4bbad\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Unknown option job-uuid=urn:uuid:f60a3de5-4428-3856-5991-fbc69dc4bbad.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Pondering option \'job-originating-host-name=localhost\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Unknown option job-originating-host-name=localhost.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Pondering option \'date-time-at-creation=\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Unknown option date-time-at-creation=.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Pondering option \'date-time-at-processing=\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Unknown option date-time-at-processing=.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Pondering option \'time-at-creation=1539685230\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Unknown option time-at-creation=1539685230.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Pondering option \'time-at-processing=1539685230\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Unknown option time-at-processing=1539685230.
D [16/Oct/2018:07:20:55 -0300] [Job 58] CM Color Calibration Mode in CUPS: Off
D [16/Oct/2018:07:20:55 -0300] [Job 58] Options from the PPD file:
D [16/Oct/2018:07:20:55 -0300] [Job 58] ================================================
D [16/Oct/2018:07:20:55 -0300] [Job 58] File: <STDIN>
D [16/Oct/2018:07:20:55 -0300] [Job 58] ================================================
D [16/Oct/2018:07:20:55 -0300] [Job 58] Filetype: PDF
D [16/Oct/2018:07:20:55 -0300] [Job 58] Neither PDF renderer command line nor Ghostscript-based renderer command line found
D [16/Oct/2018:07:20:55 -0300] [Job 58] Driver does not understand PDF input, converting to PostScript
D [16/Oct/2018:07:20:55 -0300] [Job 58] Storing temporary files in /tmp
D [16/Oct/2018:07:20:55 -0300] [Job 58] Starting process \"pdf-to-ps\" (generation 1)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Printer make and model: HP HP LaserJet 1022
D [16/Oct/2018:07:20:55 -0300] [Job 58] Switching to Poppler\'s pdftops instead of Ghostscript for old HP LaserJet (\"LaserJet <number>\", no letters before <number>) printers to work around bugs in the printer\'s PS interpreters
D [16/Oct/2018:07:20:55 -0300] [Job 58] Running command line for pstops: pstops 58 anonymous \'Test Page\' 1 \' job-uuid=urn:uuid:f60a3de5-4428-3856-5991-fbc69dc4bbad job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1539685230 time-at-processing=1539685230\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Using image rendering resolution 600 dpi
D [16/Oct/2018:07:20:55 -0300] [Job 58] Running command line for pdftops: pdftops -level2 -origpagesizes -nocenter -r 600 /tmp/foomatic-LUY4ua -
D [16/Oct/2018:07:20:55 -0300] [Job 58] Started filter pdftops (PID 13198)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Started filter pstops (PID 13199)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Syntax Warning: Unknown font type: \'???\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Syntax Warning: Substituting font \'Times-Roman\' for \'null\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Syntax Warning: Unknown font type: \'???\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Syntax Warning: Unknown font type: \'???\'
D [16/Oct/2018:07:20:55 -0300] [Job 58] Page = 595x842; 11,11 to 584,831
D [16/Oct/2018:07:20:55 -0300] [Job 58] slow_collate=0, slow_duplex=0, slow_order=0
D [16/Oct/2018:07:20:55 -0300] [Job 58] Before copy_comments - %!PS-Adobe-3.0
D [16/Oct/2018:07:20:55 -0300] [Job 58] %!PS-Adobe-3.0
D [16/Oct/2018:07:20:55 -0300] [Job 58] %Produced by poppler pdftops version: 0.62.0 ([http://poppler.freedesktop.org](http://poppler.freedesktop.org))
D [16/Oct/2018:07:20:55 -0300] [Job 58] %%LanguageLevel: 2
D [16/Oct/2018:07:20:55 -0300] [Job 58] %%DocumentSuppliedResources: (atend)
D [16/Oct/2018:07:20:55 -0300] [Job 58] %%DocumentMedia: A4 595 842 0 () ()
D [16/Oct/2018:07:20:55 -0300] [Job 58] %%BoundingBox: 0 0 595 842
D [16/Oct/2018:07:20:55 -0300] [Job 58] %%Pages: 1
D [16/Oct/2018:07:20:55 -0300] [Job 58] %%EndComments
D [16/Oct/2018:07:20:55 -0300] [Job 58] Before copy_prolog - %%BeginProlog
D [16/Oct/2018:07:20:55 -0300] [Job 58] Before copy_setup - %%BeginSetup
D [16/Oct/2018:07:20:55 -0300] [Job 58] Filetype: PostScript
D [16/Oct/2018:07:20:55 -0300] [Job 58] Reading PostScript input ...
D [16/Oct/2018:07:20:55 -0300] [Job 58] --> This document is DSC-conforming!
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found %RBINumCopies: 1
D [16/Oct/2018:07:20:55 -0300] [Job 58] -----------
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginProlog
D [16/Oct/2018:07:20:55 -0300] [Job 58] Inserting option code into \"Prolog\" section.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%EndProlog
D [16/Oct/2018:07:20:55 -0300] [Job 58] -----------
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginSetup
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *Quality normal
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Quality=normal
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: Quality=normal
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Quality=normal
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *halftone default
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: halftone=default
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: halftone=default
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: halftone=default
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *Resolution 1200x600dpi
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Resolution=1200x600dpi
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: Resolution=1200x600dpi
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Resolution=1200x600dpi
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *PageSize A4
D [16/Oct/2018:07:20:55 -0300] [Job 58] Before page loop - %%Page: 1 1
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: PageSize=A4
D [16/Oct/2018:07:20:55 -0300] [Job 58] Copying page 1...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: PageSize=A4
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *InputSlot Auto
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: InputSlot=Auto
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] pagew = 572.3, pagel = 819.3
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: InputSlot=Auto
D [16/Oct/2018:07:20:55 -0300] [Job 58] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: InputSlot=Auto
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] PageLeft = 11.3, PageRight = 583.7
D [16/Oct/2018:07:20:55 -0300] [Job 58] PageTop = 830.7, PageBottom = 11.3
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *MediaType Standard
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: MediaType=Standard
D [16/Oct/2018:07:20:55 -0300] [Job 58] PageWidth = 595.0, PageLength = 842.0
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: MediaType=Standard
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: MediaType=Standard
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *Density Density3
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Density=Density3
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: Density=Density3
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Density=Density3
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *NupOrient port
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: NupOrient=port
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: NupOrient=port
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: NupOrient=port
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *NupPages 1up
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: NupPages=1up
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: NupPages=1up
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: NupPages=1up
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginFeature: *Copies 1
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Copies=1
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %% FoomaticRIPOptionSetting: Copies=1
D [16/Oct/2018:07:20:55 -0300] [Job 58] Option: Copies=1
D [16/Oct/2018:07:20:55 -0300] [Job 58] Setting option
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%EndSetup
D [16/Oct/2018:07:20:55 -0300] [Job 58] -----------
D [16/Oct/2018:07:20:55 -0300] [Job 58] New page: %%Page: 1 1
D [16/Oct/2018:07:20:55 -0300] [Job 58] \"Setup\" section is missing, inserting it.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Inserting option code into \"Setup\" section.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Found: %%BeginPageSetup
D [16/Oct/2018:07:20:55 -0300] [Job 58] Inserting option code into \"PageSetup\" section.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Wrote 1 pages...
D [16/Oct/2018:07:20:55 -0300] [Job 58] PID 13198 (pdftops) exited with no errors.
D [16/Oct/2018:07:20:55 -0300] [Job 58] PID 13199 (pstops) exited with no errors.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Flushing FIFO.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Starting renderer with command: \"foo2zjs-wrapper -z1 -P -L0     -r1200x600 -p9 -T3 -m1 -s7   -n1 \"
D [16/Oct/2018:07:20:55 -0300] [Job 58] Starting process \"kid3\" (generation 1)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Starting process \"kid4\" (generation 2)
D [16/Oct/2018:07:20:55 -0300] [Job 58] Starting process \"renderer\" (generation 2)
D [16/Oct/2018:07:20:55 -0300] [Job 58] JCL: \033%-12345X@PJL
D [16/Oct/2018:07:20:55 -0300] [Job 58] <job data> 
D [16/Oct/2018:07:20:55 -0300] [Job 58] ./base/gsicc_manage.c:1244: gsicc_open_search(): Could not find default_gray.icc 
D [16/Oct/2018:07:20:55 -0300] [Job 58] | ./base/gsicc_manage.c:2261: gsicc_init_iccmanager(): cannot find default icc profile
D [16/Oct/2018:07:20:55 -0300] [Job 58] ./base/gsicc_manage.c:1244: gsicc_open_search(): Could not find default_gray.icc 
D [16/Oct/2018:07:20:55 -0300] [Job 58] | ./base/gsicc_manage.c:2025: gsicc_set_device_profile(): cannot find device profile
D [16/Oct/2018:07:20:55 -0300] [Job 58] **** Unable to open the initial device, quitting.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Not a pbm file!
D [16/Oct/2018:07:20:55 -0300] [Job 58] renderer exited with status 0
D [16/Oct/2018:07:20:55 -0300] [Job 58] Read 324 bytes of print data...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Wrote 324 bytes of print data...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Process is dying with \"kid4 exited with status 0
D [16/Oct/2018:07:20:55 -0300] [Job 58] kid3 finished
```
D [16/Oct/2018:07:20:55 -0300] [Job 58] Encountered error Broken pipe during fwrite\", exit stat 1
D [16/Oct/2018:07:20:55 -0300] [Job 58] Cleaning up...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Killing pdf-to-ps
D [16/Oct/2018:07:20:55 -0300] [Job 58] Read 56 bytes of back-channel data...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Read 59 bytes of back-channel data...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Read 26 bytes of back-channel data...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Read 44 bytes of back-channel data...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Read 59 bytes of back-channel data...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Killing kid3
D [16/Oct/2018:07:20:55 -0300] [Job 58] Sent 324 bytes...
D [16/Oct/2018:07:20:55 -0300] [Job 58] PID 13190 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Hint: Try setting the LogLevel to "debug" to find out more.
D [16/Oct/2018:07:20:55 -0300] [Job 58] Waiting for read thread to exit...
D [16/Oct/2018:07:20:55 -0300] [Job 58] Read thread still active, aborting the pending read...
D [16/Oct/2018:07:20:55 -0300] [Job 58] PID 13191 (/usr/lib/cups/backend/usb) exited with no errors.
D [16/Oct/2018:07:20:55 -0300] [Job 58] End of messages
D [16/Oct/2018:07:20:55 -0300] [Job 58] printer-state=3(idle)
D [16/Oct/2018:07:20:55 -0300] [Job 58] printer-state-message="Filter failed"
D [16/Oct/2018:07:20:55 -0300] [Job 58] printer-state-reasons=none

---

### Post by angelo16 on 2018-10-17
Stuck now with the Filter Failed....

Simply I can't believe that after allowing to upgrade to 18.04.1 I cannot print anything else.

---

### Post by angelo16 on 2018-10-17
here it goes the fix ... found in [https://askubuntu.com/questions/1080720/printer-filter-failed/1080926#1080926](https://askubuntu.com/questions/1080720/printer-filter-failed/1080926#1080926)

[COLOR=#242729][FONT=Arial]sudo rmdir /usr/share/ghostscript/9.25/iccprofiles[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]sudo apt-get install --reinstall libgs9-common




[/FONT][/COLOR]

---

