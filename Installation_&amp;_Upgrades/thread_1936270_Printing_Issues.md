---
title: "Printing Issues"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by makaveli0129 on 2012-03-05
Hey all i have lexmark x5070 printer and i am trying to get it to work on ubuntu 10.04 after downgrading from 11.10 since there was some bug in system-config-printer but that's neither here nor there. For the death of me it has been over a month now and i still cannot get this thing to work so any help would be much appriciated. The error logs for cups shows the following below. I followed the directions located here: [http://ubuntuforums.org/showthread.php?t=1444847](http://ubuntuforums.org/showthread.php?t=1444847) but that doesn't work either. Any ideas?

```

D [05/Mar/2012:18:10:16 -0500] [Job 14] The following messages were recorded from 06:09:32 PM to 06:10:13 PM
D [05/Mar/2012:18:10:16 -0500] [Job 14] Adding start banner page "none".
D [05/Mar/2012:18:10:16 -0500] [Job 14] Adding end banner page "none".
D [05/Mar/2012:18:10:16 -0500] [Job 14] File of type application/postscript queued by "jr".
D [05/Mar/2012:18:10:16 -0500] [Job 14] hold_until=0
D [05/Mar/2012:18:10:16 -0500] [Job 14] Queued on "Lexmark--5000-Series" by "jr".
D [05/Mar/2012:18:10:16 -0500] [Job 14] job-sheets=none,none
D [05/Mar/2012:18:10:16 -0500] [Job 14] argv[0]="Lexmark--5000-Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] argv[1]="14"
D [05/Mar/2012:18:10:16 -0500] [Job 14] argv[2]="jr"
D [05/Mar/2012:18:10:16 -0500] [Job 14] argv[3]="Test Page"
D [05/Mar/2012:18:10:16 -0500] [Job 14] argv[4]="1"
D [05/Mar/2012:18:10:16 -0500] [Job 14] argv[5]="PageSize=Letter job-uuid=urn:uuid:49807012-3c71-3411-4d1a-a50f44f94314 job-originating-host-name=localhost"
D [05/Mar/2012:18:10:16 -0500] [Job 14] argv[6]="/var/spool/cups/d00014-001"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[8]="HOME=/var/spool/cups/tmp"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[10]="SERVER_ADMIN=root@jr-desktop"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[11]="SOFTWARE=CUPS/1.4.3"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[13]="TZ=America/Detroit"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[14]="USER=root"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[17]="IPP_PORT=631"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[18]="CHARSET=utf-8"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[19]="LANG=en_US.UTF-8"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[20]="PPD=/etc/cups/ppd/Lexmark--5000-Series.ppd"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[21]="RIP_MAX_CACHE=1030098k"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[22]="CONTENT_TYPE=application/postscript"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[23]="DEVICE_URI=usb://Lexmark/5000%20Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[24]="PRINTER_INFO=Lexmark  5000 Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[25]="PRINTER_LOCATION="
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[26]="PRINTER=Lexmark--5000-Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[27]="CUPS_FILETYPE=document"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[28]="FINAL_CONTENT_TYPE=printer/Lexmark--5000-Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] Started filter /usr/lib/cups/filter/pstopdf (PID 7677)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Started filter /usr/lib/cups/filter/pdftopdf (PID 7678)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Started filter /usr/lib/cups/filter/pdftoraster (PID 7679)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Started filter /usr/lexinkjet/08zero/bin/printdriver (PID 7680)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Started backend /usr/lib/cups/backend/usb (PID 7681)
D [05/Mar/2012:18:10:16 -0500] [Job 14] pstopdf 6 args: 14 jr Test Page 1 PageSize=Letter job-uuid=urn:uuid:49807012-3c71-3411-4d1a-a50f44f94314 job-originating-host-name=localhost /var/spool/cups/d00014-001
D [05/Mar/2012:18:10:16 -0500] [Job 14] PPD: /etc/cups/ppd/Lexmark--5000-Series.ppd
D [05/Mar/2012:18:10:16 -0500] [Job 14] STATE: +connecting-to-device
D [05/Mar/2012:18:10:16 -0500] [Job 14] Printer using device file "/dev/usblp0"...
D [05/Mar/2012:18:10:16 -0500] [Job 14] STATE: -connecting-to-device
D [05/Mar/2012:18:10:16 -0500] [Job 14] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0xb777db40)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Resolution: 
D [05/Mar/2012:18:10:16 -0500] [Job 14] Page size: Letter
D [05/Mar/2012:18:10:16 -0500] [Job 14] Width: 612.00, height: 792.00, absolute margins: 18.00, 36.00, 594.00, 787.20
D [05/Mar/2012:18:10:16 -0500] [Job 14] Relative margins: 18.00, 36.00, 18.00, 4.80
D [05/Mar/2012:18:10:16 -0500] [Job 14] PPD options: -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00
D [05/Mar/2012:18:10:16 -0500] [Job 14] PostScript to be injected: 
D [05/Mar/2012:18:10:16 -0500] [Job 14] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 -sOutputFile=-  -c .setpdfwrite -f -
D [05/Mar/2012:18:10:16 -0500] [Job 14] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -sOutputType=5 -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=1 -dcupsRowFeed=1 -dcupsRowStep=1 -scupsPageSizeName=Letter -c -f -_
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[8]="HOME=/var/spool/cups/tmp"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[10]="SERVER_ADMIN=root@jr-desktop"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[11]="SOFTWARE=CUPS/1.4.3"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[12]="TZ=America/Detroit"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[13]="USER=root"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[16]="IPP_PORT=631"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[17]="CHARSET=utf-8"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[18]="LANG=en_US.UTF-8"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[19]="PPD=/etc/cups/ppd/Lexmark--5000-Series.ppd"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[20]="RIP_MAX_CACHE=1030098k"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[21]="CONTENT_TYPE=application/postscript"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[22]="DEVICE_URI=usb://Lexmark/5000%20Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[23]="PRINTER_INFO=Lexmark  5000 Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[24]="PRINTER_LOCATION="
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[25]="PRINTER=Lexmark--5000-Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[26]="CUPS_FILETYPE=document"
D [05/Mar/2012:18:10:16 -0500] [Job 14] envp[27]="FINAL_CONTENT_TYPE=printer/Lexmark--5000-Series"
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_put_params(0xb63c903c, 0xbfdf04b8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_set_color_info(0xb63c903c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[0] = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[65535] = 1
D [05/Mar/2012:18:10:16 -0500] [Job 14] num_components = 1, depth = 1
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsColorSpace = 3, cupsColorOrder = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsBitsPerPixel = 1, cupsBitsPerColor = 1
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_gray = 1, dither_grays = 2
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_color = 0, dither_colors = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] Updating PageSize to [612 792]...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting initial media size, [612 792] = 5100x6600 pixels...
D [05/Mar/2012:18:10:16 -0500] [Job 14] ppd = (nil)
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612.000 792.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] margins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWResolution = [ 600.000 600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_put_params(0xb63c903c, 0xbfdf04b8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting OutputType to "5"...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting cupsBitsPerColor to 8...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting cupsColorOrder to 0...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting cupsColorSpace to 1...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting cupsCompression to 1...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting cupsRowFeed to 1...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting cupsRowStep to 1...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting cupsPageSizeName to "Letter"...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_set_color_info(0xb63c903c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[0] = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[65535] = 255
D [05/Mar/2012:18:10:16 -0500] [Job 14] num_components = 3, depth = 24
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsColorSpace = 1, cupsColorOrder = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_gray = 0, dither_grays = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_color = 255, dither_colors = 256
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting initial media size, [612 792] = 5100x6600 pixels...
D [05/Mar/2012:18:10:16 -0500] [Job 14] ppd = (nil)
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612.000 792.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] margins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWResolution = [ 600.000 600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_open(0xb63c903c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Processing page 1...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_set_color_info(0xb63c903c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[0] = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[65535] = 255
D [05/Mar/2012:18:10:16 -0500] [Job 14] num_components = 3, depth = 24
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsColorSpace = 1, cupsColorOrder = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_gray = 0, dither_grays = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_color = 255, dither_colors = 256
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_space_params(0xb63c903c, 0xbfdf03dc)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cache_size = 1054820352
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0478)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0428)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf04d8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf03e8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0498)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0448)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 5100, height = 6600
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_put_params(0xb63c903c, 0xbfdf04b8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting LeadingEdge to 0...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_set_color_info(0xb63c903c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[0] = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[65535] = 255
D [05/Mar/2012:18:10:16 -0500] [Job 14] num_components = 3, depth = 24
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsColorSpace = 1, cupsColorOrder = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_gray = 0, dither_grays = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_color = 255, dither_colors = 256
D [05/Mar/2012:18:10:16 -0500] [Job 14] Updating PageSize to [612 792]...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.Duplex = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.Tumble = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->page = 1
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->PPD = 0x8d4bdf8
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->PPD->flip_duplex = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] (4) Flip: X=0 Y=0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.cupsPageSizeName = Letter
D [05/Mar/2012:18:10:16 -0500] [Job 14] size = Letter
D [05/Mar/2012:18:10:16 -0500] [Job 14] margins[] = [ 0.250000 0.500000 0.250000 0.066666 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] Reallocating memory, [612 792] = 4800x6260 pixels...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_space_params(0xb63c903c, 0xbfdf011c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cache_size = 1054820352
D [05/Mar/2012:18:10:16 -0500] [Job 14] Reallocated memory, [612 792] = 4800x6260 pixels...
D [05/Mar/2012:18:10:16 -0500] [Job 14] ppd = 0x8d4bdf8
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612.000 792.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] margins = [ 0.250 0.500 0.250 0.067 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWResolution = [ 600.000 600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf03f8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf03a8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0478)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0428)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf04c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf04d8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf04b0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf03e8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0448)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_put_params(0xb63c903c, 0xbfdf09a8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting LeadingEdge to 0...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_set_color_info(0xb63c903c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[0] = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[65535] = 255
D [05/Mar/2012:18:10:16 -0500] [Job 14] num_components = 3, depth = 24
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsColorSpace = 1, cupsColorOrder = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_gray = 0, dither_grays = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_color = 255, dither_colors = 256
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_put_params(0xb63c903c, 0xbfdf09a8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Setting LeadingEdge to 0...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_set_color_info(0xb63c903c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[0] = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->EncodeLUT[65535] = 255
D [05/Mar/2012:18:10:16 -0500] [Job 14] num_components = 3, depth = 24
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsColorSpace = 1, cupsColorOrder = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_gray = 0, dither_grays = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] max_color = 255, dither_colors = 256
D [05/Mar/2012:18:10:16 -0500] [Job 14] Updating PageSize to [612 792]...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.Duplex = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.Tumble = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->page = 1
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->PPD = 0x8d4bdf8
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->PPD->flip_duplex = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] (4) Flip: X=0 Y=0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.cupsPageSizeName = Letter
D [05/Mar/2012:18:10:16 -0500] [Job 14] size = Letter
D [05/Mar/2012:18:10:16 -0500] [Job 14] margins[] = [ 0.250000 0.500000 0.250000 0.066666 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] Reallocating memory, [612 792] = 4800x6260 pixels...
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_space_params(0xb63c903c, 0xbfdf060c)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cache_size = 1054820352
D [05/Mar/2012:18:10:16 -0500] [Job 14] Reallocated memory, [612 792] = 4800x6260 pixels...
D [05/Mar/2012:18:10:16 -0500] [Job 14] ppd = 0x8d4bdf8
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612.000 792.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] margins = [ 0.250 0.500 0.250 0.067 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWResolution = [ 600.000 600.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0968)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0918)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf09b8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf09c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf08d8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0938)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf0938)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_matrix(0xb63c903c, 0xbfdf02c8)
D [05/Mar/2012:18:10:16 -0500] [Job 14] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1
D [05/Mar/2012:18:10:16 -0500] [Job 14] width = 4800, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] HWMargins = [ 18.000 36.000 18.000 4.800 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6560.000 ]
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_get_params(0xb63c903c, 0xbfdf09a0)
D [05/Mar/2012:18:10:16 -0500] [Job 14] before gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] after gdev_prn_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] Leaving cups_get_params()
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_print_pages(0xb63c903c, 0xb6ea74e0, 1)
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsBitsPerPixel = 24, cupsWidth = 4800, cupsBytesPerLine = 14400, srcbytes = 14400
D [05/Mar/2012:18:10:16 -0500] [Job 14] cupsWidth = 4800, cupsHeight = 6260, cupsBytesPerLine = 14400
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.Duplex = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->header.Tumble = 0
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->page = 1
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups->PPD = 0x8d4bdf8
D [05/Mar/2012:18:10:16 -0500] [Job 14] cups_print_chunked: xflip = 0, yflip = 0, height = 6260
D [05/Mar/2012:18:10:16 -0500] [Job 14] Read 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] STATE: -media-empty-warning
D [05/Mar/2012:18:10:16 -0500] [Job 14] STATE: -offline-report
D [05/Mar/2012:18:10:16 -0500] [Job 14] Printer is now online.
D [05/Mar/2012:18:10:16 -0500] [Job 14] Wrote 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Read 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Wrote 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Read 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Wrote 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Read 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Wrote 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Read 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Wrote 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Read 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Wrote 8 bytes of print data...
D [05/Mar/2012:18:10:16 -0500] [Job 14] Set job-printer-state-message to "The Printer cannot communicate with the computer.", current level=ERROR
D [05/Mar/2012:18:10:16 -0500] [Job 14] End of messages
D [05/Mar/2012:18:10:16 -0500] [Job 14] printer-state=3(idle)
D [05/Mar/2012:18:10:16 -0500] [Job 14] printer-state-message="The Printer cannot communicate with the computer."
D [05/Mar/2012:18:10:16 -0500] [Job 14] printer-state-reasons=none

```

---

