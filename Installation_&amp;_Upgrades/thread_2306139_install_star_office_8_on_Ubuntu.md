---
title: "install star office 8 on Ubuntu"
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by weirdygeekpsych on 2015-12-12
How to install star office 8( no libre office ) on Ubuntu in 14 Lts or 10.4 lts ?

Pls  Help me with this. I have been trying to install this from past one week. 
 
Am wholly new to Ubuntu , so if there any articles suggest me that. 
Hoping for a perfect solution

---

### Post by grahammechanical on 2015-12-12
Ubuntu 10.04 reached end of life 9th May 2013. Its software repositories have been closed and archived.

Is this Star Office for Linux? Or for Windows or Mac? Has it been packaged as a Debian package (as a deb file). Do you have any instructions explaining how to install this application?

If there is a deb file then it should be possible to open the File Manager and browse to the location of the deb file, select it and right click and then select open with Ubuntu Software Centre. That might do it.

If you have been attempting to do this on Ubuntu 10.04 then it could be that the reason why it fails is down to the closure of the 10.04 repositories. They are now at a new location. You have to change the URLs of the software repositories to old-releases.ubuntu.com/ubuntu

The failure to install this application on 14.04 could be due to it not being developed anymore and so the 14.04 repositories do not contain the libraries that it needs.

Regards.

---

### Post by yancek on 2015-12-12
The link below is to instructions on how to install it on Ubuntu assuming you already have the installation media.

[https://help.ubuntu.com/community/StarOffice](https://help.ubuntu.com/community/StarOffice)

---

### Post by weirdygeekpsych on 2015-12-12
Alright!!!  After lot of searching I got star office 8 as RPM files through ISO.  Then from the extracted ISO files I got one of folder named as RPMS , in that the  star Office 8 writer,  calc, impress were there as rpm.  Got alien and converted  but the thing is i was able to convert only the individual file not the whole package. So the star office writer 8 is installed I have seen that in software center.  But remaining RPMS Files are need to be converted to open the star office 8 window ? What can I do for those?  I can't run alien  for all the necessary files need for the support of open star office window. Or is there any easy way to convert and install that.

---

### Post by efflandt on 2015-12-15
StarOffice itself has not been updated for awhile [https://en.wikipedia.org/wiki/StarOffice](https://en.wikipedia.org/wiki/StarOffice) . The most recent version of StarOffice 8 was based on OpenOffice 2.4. If there is some reason that you do not want to use LibreOffice, you can still get OpenOffice from Apache [https://www.openoffice.org/](https://www.openoffice.org/) (which is now version 4.1.2).

---

