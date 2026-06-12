---
title: "Brother Scanning Fails Again"
date: 2016-11-20
forum: MINT
---

### Post by mintynz on 2016-11-20
Hi Everyone.

Again Im finding that Brother gets "Upset" with updates on my Linux Mint 17.3 Rosa system and fails to find scanner attached. 
menu>Graphics>Xsane or Simple Scan.
Error>No Devices available.

I'm running a laser MFC-7420 and a Inkjet MFC-J430W

"Rosa" Mint is NOT a recent install so only following through current update settings, NOT installing anything passed LvL3 in Updates.

Ive Checked...

Admin > Printers - Printers are present, Test pages sent, and printed ok. - No issues

Checked Brscan - showing in Synaptic Installed
"        "     Brcsan2 - "           "      "
"         "     Brscan4 - "         "      "
"          "      Brscan-key - "      "     "
"          "   Cupswrappers Laser - Installed
"          "   LPR drivers - laser - Installed

So Now what! ](*,)

---

### Post by chris36 on 2016-11-21
chris@Z9u3 ~ $ sudo dpkg -l | grep Brother
[sudo] password for chris: 
ii  brmfcfaxlpd                                 1.0.0-2                                             i386         Brother MFC-FAX LPD driver
ii  brother-cups-wrapper-common                 1.0.0-10-0ubuntu6                                   amd64        Common files for Brother cups wrapper packages
ii  brother-udev-rule-type1                     1.0.0-1                                             all          Brother udev rule type 1
ii  brscan                                      0.2.4                                               amd64        Brother CUPS Printer Definitions
ii  brscan-skey                                 0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan2                                     0.2.5-1                                             amd64        Brother Scanner Driver
ii  brscan4                                     0.4.3-3                                             amd64        Brother Scanner Driver
ii  hl5450dncupswrapper                         3.0.0-1                                             i386         Brother HL-5450DN CUPS wrapper driver
ii  hl5450dnlpr                                 3.0.0-1                                             i386         Brother HL-5450DN LPR driver
ii  mfcj430wcupswrapper                         3.0.0-1                                             i386         Brother CUPS Inkjet Printer Definitions
ii  mfcj430wlpr                                 3.0.0-1                                             i386         Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                       1.3-8                                               amd64        printer driver Brother P-touch label printers

---

