---
title: "Epson Perfection 1650"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by Canuck.old on 2015-02-11
Sooo - I finally upgraded to 14.10 and then plugged in my scanner for the first
time in several years and much to my dismay the config file has been changed.
Shocking. I do remember how to look for and fix the old config file but but but
the new system leaves fewer clues as to what to do. 

So my question is "where do I find the config info for my scanner"?

Thank you for your time.

dkr

---

### Post by lidex on 2015-03-02
I'm not in KDE but try ~/.sane/xsane

---

### Post by coldraven on 2015-03-03
The howto in the first post shows how I get my EP 1670 to work. I have been using that fix for years, it always works.
Reading it again I'm not sure if it will work for your 1650. 

[http://ubuntuforums.org/archive/index.php/t-26911.html](http://ubuntuforums.org/archive/index.php/t-26911.html)

---

### Post by pdc on 2015-03-03
Hi canuck; well done on "upgrading" to 14.10 ..........the latest version ........BUT ............as I read it ............[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) ............support runs out in 6 months, so no updates or security fixes, and then best to migrate to a newer version

Some see real merit in the LTS (long-term releases): many are running 12.04 ............ stable and supported till April 2017 ..........and 14.04 is supported till April 2019 ..........saves all the headache of changes ..........

__________________--

1650 .....................looking for drivers, most find starting here is good [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and tapping in 1650 gets one to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35136&DSCCHK=de9429162c4ec47336d66db3c2c0433f55f79a46](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35136&DSCCHK=de9429162c4ec47336d66db3c2c0433f55f79a46)

and Epson say you need 2 things; in a set order;

1) firstly .............. iscan data package **[COLOR="#008000"]iscan-data_1.35.0-1_all.deb[/COLOR]** ( 3 from the bottom of the list!!)
2) [COLOR="#008000"]iscan_2.30.1-1~usb0.1.ltdl7_amd64.deb[/COLOR] or [COLOR="#008000"]iscan_2.30.1-1~usb0.1.ltdl7_i386.deb[/COLOR]

......... that seems to be all they think you need ??

---

### Post by stoobers on 2015-08-20
Hello,
I upgraded to Ubuntu 14.04.2 LTS (kubuntu) and it broke my scanner, also.
But I have a simple fix for you!
My scanner: Epson Perfection 1650
Internally, it seems to go by the name: GT-8200
I figured that out by installing simple-scan by typing:
sudo apt-get install simple-scan
then i run:
simple-scan -d (this puts it into debug mode)

You will see the GT-8200 referenced.
When you try a scan, you will also see a message like this, which is an error:
DEBUG: scanner.vala:350: Device: name="epson2:libusb:002:003" vendor="Epson" model="GT-8200" type="flatbed scanner"

This is an error, because the Epson Perfection 1650 (GT-8200) is not part of "epson2", but rather, "epson".

So we change it like this:
sudo /etc/sane.d/dll.conf
scroll down and you will see that by default "epson" is commented out and "epson2" is active.
So you need to reverse this and make it look like this:
epson
#epson2

Now, you will be able to scan.
No need for the firmeware, and no need for any updates.

Thanks,
stoobers

---

