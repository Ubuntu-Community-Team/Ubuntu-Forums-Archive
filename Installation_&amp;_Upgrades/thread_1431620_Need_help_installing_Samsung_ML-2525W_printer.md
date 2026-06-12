---
title: "Need help installing Samsung ML-2525W printer"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by dnguyen1963 on 2010-03-16
Hi,

I just purchased this Samsung printer.  There is no driver from Ubuntu.  There is a driver from Samsung website.  It is called unifiedLinuxDriver_0.92.tar.gz.  Could someone please tell me how to install this driver on my computer after I download the file?  

Thank you.

Dnguyen1963
Ubuntu 8.04 LTS

---

### Post by dnguyen1963 on 2010-03-17
> **dnguyen1963 said:**
> Hi,

I just purchased this Samsung printer.  There is no driver from Ubuntu.  There is a driver from Samsung website.  It is called unifiedLinuxDriver_0.92.tar.gz.  Could someone please tell me how to install this driver on my computer after I download the file?  

Thank you.

Dnguyen1963
Ubuntu 8.04 LTS

Anyone out there?...please!  I have tried to clicked on the autorun file and it said that I do not have permission to perform the installation.  I have logged on as an admin.

---

### Post by yellowtrain on 2010-05-11
sudo sh install.sh:popcorn:

---

### Post by jackuss_169 on 2010-05-15
Hey mate, i had the same problem, you need to get the linux drivers off the samsung website (i think its on the CD too)

then open up terminal 

type sudo -s

then type your administrator password and that will give you the super user privileges, then in the folder for the printer that you get off the site just drop the autorun into the terminal, and a 'windows style' installation sequence will happen after that, once all thats done it should work!

---

### Post by C1377 on 2011-06-18
> **jackuss_169 said:**
> Hey mate, i had the same problem, you need to get the linux drivers off the samsung website (i think its on the CD too)

then open up terminal 

type sudo -s

then type your administrator password and that will give you the super user privileges, then in the folder for the printer that you get off the site just drop the autorun into the terminal, and a 'windows style' installation sequence will happen after that, once all thats done it should work!

[http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=US&CttFileID=2541965&CDCttType=DR&ModelType=C&ModelName=ML-2525W/XAA&VPath=DR/200911/20091103171827750/UnifiedLinuxDriver_0.92.tar.gz](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=US&CttFileID=2541965&CDCttType=DR&ModelType=C&ModelName=ML-2525W/XAA&VPath=DR/200911/20091103171827750/UnifiedLinuxDriver_0.92.tar.gz)

-thanks

---

### Post by Bazon on 2011-12-30
Thanks, that helped on my old 10.04 install.

And, if anyone stumbles on this thread doing a buying decision: On 11.04 and 11.10, this printer works out of the box. :-)
Even wireless setup works without a windows pc, all you need is a LAN connection.
The manual + CD includes Linux notes, very fine. :-)

---

