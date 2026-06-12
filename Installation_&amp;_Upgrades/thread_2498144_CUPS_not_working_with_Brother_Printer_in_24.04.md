---
title: "CUPS not working with Brother Printer in 24.04"
date: 2024-06-01
forum: Installation &amp; Upgrades
---

### Post by jon-mclin on 2024-06-01
I have a fresh 24.04 install in which printing does not work (without any error messages).  The printer (a Brother Laser with wired LAN connection) shows up (automagically), but print jobs sit in "Processing" state forever.  The printer never wakes up.   This same printer has worked fine and continues to with other devices connected to the same switch (Windows 10, Mac, and my older Ubuntu 22.04 desktop). 

The computer with 24.04 is new. When I received it a couple of months ago I initially installed 23.10 (right before 24.04 was released), but then upgraded to 24.04.   I never tried to print with 23.10, but after upgrading to 24.04 I started using it as a means to take 24.04 for a test spin.  When I print, no error is reported, and the print que shows the document in the "processing" state - forever.   To determine whether this was due to the upgrade from 24.04, I did a clean 24.04 install today - printing simply does not work with 24.04 and this printer (a Brother MFC-8810DW).

The automagic printer selection does not select a driver (and I see notes in CUPS that drivers are deprecated). As a debugging step, I did try selecting a printer driver.  No change in behavior - printer que with and without the driver selected exhibited the same behavior.
(startup message in cups log:  
W [01/Jun/2024:00:00:15 -0700] Printer drivers are deprecated and will stop working in a future version of CUPS. See [https://github.com/OpenPrinting/cups/issues/103](https://github.com/OpenPrinting/cups/issues/103)
)

Any ideas on troubleshooting this issue?   I did turn CUPS debugging on, so the log files are huge.  No messages which overtly indicate an error to me.   It appears that CUPS simply is not talking to the printer, but thinks it is.   The network interface is fine for everything else, and I can connect to the printer admin web page via a browser.

This is the only printer we have on our home network now so I can't try a different printer.   The current Brother printer has worked through upgrades on the other Ubuntu box from 14.04 to 22.04.

---

### Post by lgroli on 2024-07-06
I had the same problem with my old Brother HL-2240D printer, attached to the network. I have used it for several years in 18.04 through 22.04 with no issues.
 
What solved it for me was NOT to choose the "recommended" driver in the database after the printer was detected by the system on the network. That one uses hpijs (which I saw in the cups error log was refused). I read on a forum that hpijs is not supported anymore by cups.
There was a second driver (hl1250) in the database which I chose subsequently. 
After that all worked fine. 

Maybe you are able to do the same with your printer.

---

### Post by huubb on 2024-09-01
Usually I do run a monthly check on the printers in my home office environment. This weekend I discovered that the print function for the Brother HL-L8260CDW series was broken. Searching on the internet I didn´t find a solution other then that more people reported the same.

With some research I found that the following 2 .deb packages have been deinstalled a few weeks back:
hll8260cdwcupslpr:i386 1.3.0-0 and hll8260cdwcupswrapper:i386 1.4.0-0

This gave me some more clues where / how to find a solution. Found it at the Brother support pages:
[https://support.brother.com/g/b/downloadlist.aspx?c=nl&lang=nl&prod=hll8260cdw_us_eu_as&os=128&flang=English](https://support.brother.com/g/b/downloadlist.aspx?c=nl&lang=nl&prod=hll8260cdw_us_eu_as&os=128&flang=English)

After going through the step of installing the (latest software) I have been seeing the installation of hll8260cdwcupslpr:i386 1.5.0 and hll8260cdwcupswrapper:i386 1.4.0

The HL-L8260CDW is properly working now.

My environment is Ubuntu 24.04 fully patched and up-to-date

---

### Post by tomdkat on 2024-09-01
> **huubb said:**
> With some research I found that the following 2 .deb packages have been deinstalled a few weeks back:
hll8260cdwcupslpr:i386 1.3.0-0 and hll8260cdwcupswrapper:i386 1.4.0-0

This gave me some more clues where / how to find a solution. Found it at the Brother support pages:
[https://support.brother.com/g/b/downloadlist.aspx?c=nl&lang=nl&prod=hll8260cdw_us_eu_as&os=128&flang=English](https://support.brother.com/g/b/downloadlist.aspx?c=nl&lang=nl&prod=hll8260cdw_us_eu_as&os=128&flang=English)

After going through the step of installing the (latest software) I have been seeing the installation of hll8260cdwcupslpr:i386 1.5.0 and hll8260cdwcupswrapper:i386 1.4.0

The HL-L8260CDW is properly working now.

My environment is Ubuntu 24.04 fully patched and up-to-date

Glad it's working for you now!  I also use a Brother printer and was going to suggest installing the software from Brother.   :)  

Peace...

---

