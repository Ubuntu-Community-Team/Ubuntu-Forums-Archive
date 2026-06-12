---
title: "Install Printer Lexmark S305"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by Davidslv on 2010-08-14
Hi, i bought this Printer [http://support.lexmark.com/index?page=content&productCode=LEXMARK_IMPACT_S305&actp=RECOMMEND&id=DR20679&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_IMPACT_S305&actp=RECOMMEND&id=DR20679&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en)

But now that i look it only supports rpm distros (at least it seems).

There is anyway to install it in my ubuntu ?

I downloaded the file, but it gives-me errors, i tried trought CUPS but there is no drivers for this printer...

the errors :

> david@Notebook:~/Downloads$ sh Lexmark_S300-S400_Series_E060810_00_FWUpdate.i386.sh
Lexmark_S300-S400_Series_E060810_00_FWUpdate.i386.sh: 11: function: not found
Firmware Update Utility

Usage: <fuu> -m <1,2> -d <device1,device2,...> -l <1/2> -e <1/2>

david@Notebook:~/Downloads$ ./Lexmark_S300-S400_Series_E060810_00_FWUpdate.i386.sh 
./Lexmark_S300-S400_Series_E060810_00_FWUpdate.i386.sh: line 83: --error: command not foundThank you for your help

---

### Post by Frogs Hair on 2010-08-14
This is old , but it's all I can find.  [URL="http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/"]http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/ 
[/URL]

---

### Post by halj32 on 2010-08-14
if you looked properly you would have found this link for deb
[http://support.lexmark.com/index?page=content&productCode=LEXMARK_IMPACT_S305&actp=RECOMMEND&id=DR20547&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_IMPACT_S305&actp=RECOMMEND&id=DR20547&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en)

download
[http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_IMPACT_S305&id=DR20547&segment=DOWNLOAD&userlocale=EN_US&locale=en&oslocale=en_US](http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_IMPACT_S305&id=DR20547&segment=DOWNLOAD&userlocale=EN_US&locale=en&oslocale=en_US)


the page link
[http://support.lexmark.com/index?locale=en&userlocale=EN_US&productCode=LEXMARK_IMPACT_S305&page=recommendedDownloads&segment=DOWNLOAD#2](http://support.lexmark.com/index?locale=en&userlocale=EN_US&productCode=LEXMARK_IMPACT_S305&page=recommendedDownloads&segment=DOWNLOAD#2)

this is for 32bit version
goodluck

---

### Post by Davidslv on 2010-08-16
Thanks **halj32**,

I really didn't saw that page, and i really search several times...

Thanks, i'm going to try when i get home.

---

### Post by Kaboontu on 2011-02-25
i had the same problem
dl the right drivers form lexmark support page
then untar
and open terminal

sudo -i sh, then space, and copy paste the driver
cancel the first attemtp to run
and then give sudo pass
follow instructions. all gut.

---

### Post by chorltoon on 2011-06-03
Seems like this isn't the only problem we will have if running Ubuntu 11.04. Found this and hope it might help someone:

[http://dylanmtaylor.com/2011/04/17/fixing-lexmark-printer-driver-installation-in-ubuntu-11-04/]("http://dylanmtaylor.com/2011/04/17/fixing-lexmark-printer-driver-installation-in-ubuntu-11-04/")

A broken driver due to a typo!

---

