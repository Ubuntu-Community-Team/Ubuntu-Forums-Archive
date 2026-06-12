---
title: "Epson SX218 scanner not working"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by lawsos01 on 2011-03-23
Installing all-in-one Epson SX218 on Ubuntu 10.10, printer and copier works fine but cannot get the scanner to work.  Simple Scan gives error "Failed to scan. No scanners available. Please connect a scanner" 

This model does not show up on compatibility lists I've seen but I'm *sure* I've seen a post describing how to make this work (obviously can't find it now) 

thanks in advance.....

Stuart

---

### Post by jonkirton on 2011-06-20
I found this site, it works for me on Maverick.

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo)

I needed to restart after I installed.

---

### Post by EduardoCR on 2011-07-25
Hi. I'm relatively new to Ubuntu, and I share the Epson SX218 scanner problem. When I installed Ubuntu and then connected the Epson multi-function via USB, the printer drivers installed very smoothly, no problems whatsoever. But then I realized that the scanner part just wasn't there. The system didn't recognize it. Searching through the help forums, I found your comment, and although it's been a while since it was posted, I've followed your link and browsed through Avasys. To cut a long story short, I've followed every step of the process and still no luck. XSane software still thinks there's no scanner connected. Is there anything I can do to overcome this ? Is there any info you need from my part to assess the situation ?

---

### Post by NilsOscar on 2011-10-08
I have the exact same problem. "Failed to scan". "No scanners available. Please connect a scanner". I downloaded the iscan-plugin-gt-x820_2.1.2-1_amd64.deb. Was that wrong? I have an Intel 64 bit processor and Ubuntu 11.04 64 bit OS on an Vaio Laptop. I have the Epson V600. scanner

---

### Post by NilsOscar on 2011-10-08
I don't think this helps anyone, but I did plug in my Epson RX500 (Scanner and printer) and I Managed to scan from it. Bummer because I want to scan 120 (medium format) film, which the RX500 does not handle.

---

### Post by GSD4ME on 2013-03-21
Appended my bit to this thread as I am having the same problem not getting the scanner to work on my Epson SX218.

I followed (a couple) of threads re: this problem and came to a couple of pages:

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and I selected the "scanner driver" option and clicked "download"

This took me to this page:

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435)

So I clicked "accept"
Then I get given a *whole list* of items that I have no idea whether to download some or all of them.

How do I know which file to download so I can get the scanner software?

Many thanks

---

### Post by pdc on 2013-03-22
a forum moderator is likely to close this thread very shortly; as it is 18 months old......... the moderators hover overhead.......watching all ..............................

first thing you need is to install the DATA PACKAGE: **[COLOR="#008000"]iscan-data_1.22.0-1_all.deb[/COLOR]** .....it is at the bottom of the list ...................
...........then..................... if 32bit system, you need [COLOR="#008000"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR] and if 64bit you need [COLOR="#008000"]iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb[/COLOR] ...........the [COLOR="#EE82EE"]ltd7[/COLOR] refers to newer kernels .......

I suggest you download and read [COLOR="#008000"]**userg_revQ_e.pdf**[/COLOR] as it is a pdf of instructions and is very detailed if you so need it ..............

If you download the data.deb to your Downloads directory and the appropriate ltd7.deb you can install them by right-clicking on each package, and selecting "install with gdebi installer...................."

If you need more advice, you will likely need to start a new thread...................

---

