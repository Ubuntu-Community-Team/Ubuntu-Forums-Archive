---
title: "Anti-Virus Software?"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by thefallofroy on 2010-03-17
I know that it's practically impossible to get a virus in Ubuntu, but just for S&Gs is there any anti virus software that works with Ubuntu to scan for viruses?

---

### Post by howefield on 2010-03-17
Clamav is in the repository, so can be installed with Synaptic Package Manger, and most of the "big" anti virus vendors do  linux version. AVG and Avast do free versions also.

---

### Post by MelDJ on 2010-03-17
see: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by thefallofroy on 2010-03-19
Thanks for the help!

---

### Post by jskandhari on 2010-03-19
In any Case The virus File which is downloaded in Linux won't be execute thus the virus won't affect unless it has be executed via Windows... So if the Virus lands in a NTFS/FAt partition and then which is executed in Windows and again you come back to Linux Clamv will detect it...

Elsewise Clamv is a good virus scanner and deleter... infact i Scan my Windows partitions via it only and don't use any antivirus in the Windows and All my windows are Running Perfect for past 3 yrs :)

---

### Post by thefallofroy on 2010-03-19
Thanks for the tip jskandhari

---

### Post by jimmers on 2010-03-20
Give Bitdefender a try:-
  	 	 	 	 	 	 	  **What is BitDefender ?**

  BitDefender is a program to check for Windows viruses and malware. It can be run in the background or on demand when required. Once installed it can be found under Applications - Systems Tools. It can be used as an alternative to clamav/clamtk.  
 **Installation**

  Add the repository by going to System - Administration - Software Sources, click on the 'Third Party Software' tab. Now click on 'Add' and enter  
 deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free  Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). Now in Applications - Accessories - Terminal add the repository key:  
 wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc) sudo apt-key add bd.key.asc  Now update the apt cache with  
 sudo apt-get update  Install the graphical interface and command line program with  
 sudo apt-get install bitdefender-scanner-gui Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications - System Tools - BitDefender Scanner).  
 Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button. 



You have to have a license key:
   	 	 	 	 	 	  download from [http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html), which has an orange download button which takes you to a page where you complete the details for a free licence. You must supply a real email address because the actual download link and free licence key will be emailed to you.
 
 Hope it helps

---

### Post by mvelte54 on 2010-03-20
I personally like klamav. You can get it through synaptic. It's made by clamav just a little more user friendly.

---

### Post by Tikkyca on 2010-03-20
Try virus scanner i from ubuntu software center.

---

### Post by fonsi2099 on 2011-10-18
Dear Sirs, After runing Clamv, I get the following warning/ virus:
PUA.JS.Xored, 

what can we do to avoid that?

thank you
;)

---

### Post by crazy bird on 2011-10-18
> **mvelte54 said:**
> I personally like klamav. You can get it through synaptic. It's made by clamav just a little more user friendly.
 
And it even comes with a GUI: clamtk.
 
Links:
[http://www.sucka.net/2010/03/two-front-ends-for-clamav/](http://www.sucka.net/2010/03/two-front-ends-for-clamav/)
[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)
[http://freshmeat.net/projects/clamtk/](http://freshmeat.net/projects/clamtk/)

---

### Post by crazy bird on 2011-10-18
> **fonsi2099 said:**
> Dear Sirs, After runing Clamv, I get the following warning/ virus:
PUA.JS.Xored, 
 
what can we do to avoid that?
 
thank you
;)
 
Check here: [http://www.google.nl/search?hl=nl&source=hp&q=PUA.JS.Xored&oq=PUA.JS.Xored&aq=f&aqi=&aql=&gs_sm=e&gs_upl=953l953l0l1594l1l1l0l0l0l0l0l0ll0l0](http://www.google.nl/search?hl=nl&source=hp&q=PUA.JS.Xored&oq=PUA.JS.Xored&aq=f&aqi=&aql=&gs_sm=e&gs_upl=953l953l0l1594l1l1l0l0l0l0l0l0ll0l0)

---

