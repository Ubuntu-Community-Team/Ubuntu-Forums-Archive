---
title: "[SOLVED] install/upgrade without network connection"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by fedra88 on 2008-08-07
is it possible to upgrade from 8.04 to 8.04.1 without a network connection?
and how about installing new software (openoffice)?

mind that my pc HAS NO network interfaces... i'd like to know if i can update in any other way (cd, usb stick...)

---

### Post by Partyboi2 on 2008-08-07
download the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/8.04.1/") and use that to upgrade.
> Use this method if the system being upgraded is not connected to the Internet.  
 
[LIST=1]
[*] 	 	Download and burn the alternate installation CD.  	
[*] 	 	Insert it into your CD-ROM drive.  	
[*] 	 	A dialog will be displayed offering you the opportunity to upgrade using that CD.  	
[*] 	 	Follow the on-screen instructions.  	
[/LIST]
  If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:  
 gksu "sh /cdrom/cdromupgrade"
 Or in Kubuntu run the following command using Alt+F2:  
 kdesu "sh /cdrom/cdromupgrade"

---

### Post by fedra88 on 2008-08-07
thank you partboi2!!! solution was easier than i thought :)

and.. how about new software?

---

### Post by Partyboi2 on 2008-08-08
to install other software you can use add/remove (applications>system>add/remove) or synaptic (applications>system>synaptic package manager)

---

### Post by fedra88 on 2008-08-08
can synaptic work even without an internet connection? how does it work?

---

### Post by Partyboi2 on 2008-08-08
you can use the package generating script feature in Synaptic Package Manager. See [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") for more info. Another option you can use is [[COLOR=Blue]aptoncd[/COLOR]]("http://aptoncd.sourceforge.net/") which is another useful way of installing packages without a internet connection.

---

