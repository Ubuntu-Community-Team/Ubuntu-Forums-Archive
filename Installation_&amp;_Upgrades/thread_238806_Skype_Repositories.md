---
title: "Skype Repositories"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Yumi on 2006-08-18
To install Skype on Ubuntu the guides recommend to add to the repositories list deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free. However, the repository is not accessable and Skype does not reply to enquiries. Any advice?

Michael

---

### Post by Fass on 2006-08-18
If you can't access the repos then just download the deb from skype.com.

---

### Post by moma on 2006-08-18
The Skype repository seems to be unavailable but you can download and install the .deb package manually.

Install QT3 library first
$ [COLOR="Green"]sudo apt-get install libqt3-mt[/COLOR]

Get skype from [http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)
$ [COLOR="Green"]wget [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)[/COLOR]

Install skype
$ [COLOR="Green"]sudo dpkg -i skype_1.2.0.18-2_i386.deb[/COLOR]

---

### Post by Yumi on 2006-08-24
Finally got a reply form Skype. They are aware that the repository is not accessable! and are busy working on a solution.

Michael

---

### Post by aysiu on 2006-08-24
It's in the PLF repositories:
[http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/skype/](http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/skype/)

---

### Post by Yumi on 2006-08-24
Thanks moma for the download instruction. I followed it but the .396 version will not work on my 64bit installation.

Michael

---

### Post by aysiu on 2006-08-24
> **Yumi said:**
> Thanks moma for the download instruction. I followed it but the .396 version will not work on my 64bit installation.

Michael
Skype on 64-bit is tricky, apparently. Read more [here](http://www.ubuntuforums.org/showthread.php?t=223101).

---

