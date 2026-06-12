---
title: "xsane not working upgrade from 12.04 to 14.04"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Sherman_Willden on 2014-04-18
If xsane will be fixed later then disregard this. Xsane reports no devices available but it worked before the upgrade. I performed hp-check and hp-doctor. The doctor installed some files. Before all this I could print and lpq showed HP-Officejet-6600 is ready. Is there some set-up I need to perform for xsane?

Thank you;

---

### Post by ckrles on 2014-06-26
I have a similar problem. I can't scan on a brother DCP-7055. I can print. I downloaded and install all the drivers according to the manufacturer's instructions. No luck.

I work prperly on my old computer running 12.04 lts.

Any ideas?

I openend a thread [http://ubuntuforums.org/showthread.php?t=2231550&p=13058999#post13058999](http://ubuntuforums.org/showthread.php?t=2231550&p=13058999#post13058999)

---

### Post by SuperFreak on 2014-06-26
Same problem with my MFC 5490CN Brother printer . Found this solution which worked for that printer, HP printers would be different:
> 1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):

The lines to be added--------------------------- 


# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"


3. Restart the OS. 
[http://askubuntu.com/questions/116157/how-do-i-install-a-scanner-driver-for-a-brother-mfc-7420]("http://askubuntu.com/questions/116157/how-do-i-install-a-scanner-driver-for-a-brother-mfc-7420")

Good Luck

---

