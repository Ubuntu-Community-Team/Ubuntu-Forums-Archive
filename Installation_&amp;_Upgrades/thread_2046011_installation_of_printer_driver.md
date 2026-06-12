---
title: "installation of printer driver"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by rotem30010 on 2012-08-22
hello all,

I downloaded a printer driver (canon pixma ip1900) from cannon site. can anyone give me some guidelines on how to install the driver and aplly it to the printer?

thanks.

---

### Post by darkod on 2012-08-22
First of all, are you sure the printer is not already supported? Many people seem to rely only on plugging it in and watching if it installs automatically or not.

Even if ubuntu doesn't detect the connected printer, it doesn't mean it can't support it.

Open Printers and click the Add button and try to add it like that. There will be a list to select from, see if it's there or not. If it is there, ubuntu will download and install the correct driver.

If you need to install the driver manually, first extract it in some folder (usually they come compressed). Then see if there is a readme.txt in the extracted files. Usually the readme will have instructions how to install.

If there are no instructions, look around the folder, there might be install.sh file or similar. Usually you would start one of those by opening terminal, going to the folder in question, and execute the file putting ./ in front. Something like:
```
cd /home/username/foldername
sudo ./install.sh
```

Often you will need to use the sudo because installing a printer adds system files.

Let us know how it goes.

---

### Post by rotem30010 on 2012-08-22
hi,
i extracted the compressed libraries and sublibraries and searched for .sh files. the out put is a lot of autogen.sh files and a keytext.sh. none of them seems to be right ( i googled a little bit about autogen.sh).

btw, i searched for the automatically suggested drivers. the earliest driver version is ip2000 whereas mine is ip1900.

any input on this one? still googling...

./iP1900_debian_printer/cnijfilter-common-3.00/lgmon/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/printui/keytext.sh
./iP1900_debian_printer/cnijfilter-common-3.00/printui/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/backend/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/libs/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/cngpijmon/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/pstocanonij/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/ppd/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/cngpij/autogen.sh
./iP1900_debian_printer/cnijfilter-common-3.00/cnijfilter/autogen.sh

---

### Post by darkod on 2012-08-22
Sorry, that doesn't mean anything to me. Any instructions on the Canon website where the driver is? Or in their support section?

---

### Post by rotem30010 on 2012-08-27
I'm currently renovating so i don't have time to explore the whole thing.
What i'll do, however, is to run al autogen.sh files and hope that it will install the driver.
Also, i sent an email to canon support. I'll update on the progress.

---

### Post by rotem30010 on 2012-09-02
ok,
the answer from canon is that currently they don't support linux.
That is although they have linux driver for pixma 1900.
Again, i downloaded the driver files but i don't know how to install them.
if anyone has a tip on it i'll be thankfull.

Rotem

---

### Post by rotem30010 on 2012-09-02
Hi,
try this link. It seems very good. 
[http://all-about-linux.blogspot.co.il/2011/01/install-canon-pixma-ip-1900-1800-on.html](http://all-about-linux.blogspot.co.il/2011/01/install-canon-pixma-ip-1900-1800-on.html)

---

### Post by pdc on 2012-09-02
if you go to the Canon Asia website, 

[http://support-asia.canon-asia.com/P/search?model=PIXMA+iP1980&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+iP1980&menu=download&filter=0&tagname=g_os&g_os=Linux)

there are **two drivers** to download:

1) the **_common driver_** (called the *IJ Printer Driver Ver. 3.00 for Linux (debian Common package*)......and ..then ...
2) the specific driver for the ip1900 series (called the *IJ Printer Driver Ver. 3.00 for Linux (debian Package for iP1900series*)

both are .deb packages;

so if when one clicks to download, and gdebi installer offers to install, my recommendation would be to accept that

if you are using 32bit Ubuntu, you should find the driver is then installed

post back if you want more detailed help;

sounds as though you have downloaded these drivers? 

If they are in your Downloads directory.. if you open the directory and right click on the two packages sequentially (ie one after the other) you can select with the right click to install with gdebi installer;

install **COMMON** first and then the **ip1900** driver

you can **SUBSCRIBE** to a thread, to be notified if there is an answer for you: do you know how?

---

### Post by rotem30010 on 2012-09-27
there's a solution:

Canon iP1900 Series
Open the terminal and run these command:

sudo apt-add-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-ip1900series


the full link is: 
[http://www.upubuntu.com/2011/10/how-to-install-canon-pixma-ip1800.html](http://www.upubuntu.com/2011/10/how-to-install-canon-pixma-ip1800.html)

thanks everyone:)

---

