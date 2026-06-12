---
title: "After Upgrade to 16.04.1 All Kinds of Printing Issues"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2016-08-08
I just did a fresh install of 16.04.01 LTS

So afterwards I started installing printers.
We have a networked (wireless) HPLaserJet P1102w
A Canon MX922 (wireless)

And I use print to pdf as well.

Let's start with printing from the HP
I installed it by using 
System Settings | Printers | Add Network Printer
The installation seemed to go smoothly.
I was able to print a test page very fast. No issue

Then I tried to print a receipt from Firefox.
The print job was held.
So I went to "Document Print Status" saw the document was held and I clicked on the document, then clicked on the "Release"
[Printer Name] may not be connected error

I then tested to see if the printer was still connected by copying the page, opening Libre Office and printing using the HP printer.
It printed perfectly and immediately.

So I thought maybe it was a Firefox issue.
I opened Chromium, tried printing a webpage in my browser, and got the same error.

I can make screen prints from CUPS, or from the System Settings | Printers | [Hp 1102] if that would be helpful.

**Second Issue is for printing to PDF**

When I choose "Print to pdf" regardless of the package I use (Libre Office, any browser), it converts all text into graphics.
How do I get it to print text to pdf and have it remain text?

**Canon**
There are no issues printing from a webpage to the Canon.
I did notice when it installed it showed the Canon as an IPP Printer.
It did not show that for the HP

Thanks in advance for your assistance.

And if this is in the wrong section, feel free to move it to the right forum.

---

### Post by LaughingHorse on 2016-08-08
To add info to this post

We have another computer also using 16.04 and there is no issue printing to the HP Printer

The settings on the computer printer with problems are:
Device URL: hp:/net/HP_LaserJet_Professional_P1102w?zc=NPI001334

The settings on the computer printer wiht no problems are:
URL: hp:/net/HP_LaserJet_Professional_P1102w?zc=NPI001334a

---

### Post by LaughingHorse on 2016-08-08
I installed the HP Device Manager to see if I could get some answers

I ran Diagnose HPLIP Driver and got the following:


HP Linux Imaging and Printing System (ver. 3.16.3)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.16.3)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

There was a lot of lines with errors, I tried to post but the forum software would not let me.
So I have to just post a very small part of what I got.

--------------
| PERMISSION |
--------------
```
Missing Required Dependencies
-----------------------------
error: 'libcups2' package is missing or 'cups' service is not running.
error: 'libdbus-1-dev' package is missing/incompatible
error: 'libsnmp-dev' package is missing/incompatible
error: 'snmp-mibs-downloader' package is missing/incompatible
error: 'libusb-1.0.0-dev' package is missing/incompatible
error: 'openssl' package is missing/incompatible
error: 'libcups2-dev' package is missing or 'cups' service is not running.
error: 'cups-bsd' package is missing or 'cups' service is not running.
error: 'cups-client' package is missing or 'cups' service is not running.
error: 'libsane-dev' package is missing/incompatible
error: 'python3-dev' package is missing/incompatible
error: 'libjpeg-dev' package is missing/incompatible
error: 'libcupsimage2-dev' package is missing or 'cups' service is not running.
error: 'libtool' package is missing/incompatible
error: 'libtool-bin' package is missing/incompatible

```

Missing Optional Dependencies
-----------------------------
error: 'gtk2-engines-pixbuf' package is missing/incompatible
error: 'xsane' package is missing/incompatible

Should I uninstall and reinstall CUPS?
SHould I install libtool and 'libtool-bin from Synaptic?

Thank You In Advance For Your Reply and Help.

---

