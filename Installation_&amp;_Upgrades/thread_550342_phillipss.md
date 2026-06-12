---
title: "phillipss"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by phillipss@comcast.net on 2007-09-13
I just clicked on the update icon and received the following message:E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I tried going to the terminal mode and typed:su
entered my password and then pasted the command from the screen. Nothing happened except in terminal mode it had the > showing??
Can someone help as it would be very much appreciated.

---

### Post by Pumalite on 2007-09-13
Run: sudo dpkg --configure -a if you haven't done it. Post back with results.

---

### Post by phillipss@comcast.net on 2007-09-13
Most services that use PAM need to be restarted to use modules built for  &#9474;  
 &#9474; this new version of libpam.  Please review the following space-separated  &#9474;  
 &#9474; list of init.d scripts for services to be restarted now, and correct it   &#9474;  
 &#9474; if needed.                                                                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Among the services that require restarting are the display managers kdm,  &#9474;  
 &#9474; wdm, and xdm.  If you are upgrading from within an X session started      &#9474;  
 &#9474; with one of these display managers, restarting that service will          &#9474;  
 &#9474; terminate your X session.  It is recommended that you remove that         &#9474;  
 &#9474; service from the list here and restart it later at your convenience.      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Some other services such as xscreensaver, gnome-screensaver, and          &#9474;  
 &#9474; xlockmore cannot be restarted for you.  You will not be able to           &#9474;  
 &#9474; authenticate to these services until you restart them manually. 
now what do I select.
Bye the way, Thank you for the quick response!

---

### Post by Pumalite on 2007-09-13
I don't know how old is your installation, but I would re-install.

The pluggable nature of PAM is one reason for using dynamic linking of system binaries. However, this necessitates the availability of a recovery mechanism should a problem develop in the linker or shared libraries; for example both NetBSD and FreeBSD supply a /rescue directory containing statically linked versions of important system binaries.

---

### Post by phillipss@comcast.net on 2007-09-13
It looks like I need to restart everything after running the command suggested.
Should I reboot fresh or do a ctrl/alt/backspace?

---

### Post by phillipss@comcast.net on 2007-09-13
This is a new install of Ubuntu 7.10 Alpha 5 installed on 8/23/07.

---

### Post by Pumalite on 2007-09-13
Reboot
See my editing

---

### Post by phillipss@comcast.net on 2007-09-13
I rebooted after running the command line and was able to click on the update icon and it ran successfully!
Problem is resolved thanks to you!!
This is why I like Ubuntu, a great distribution, and if you run into a problem, lots of nice peoiple out there to help you through it.
Thank you for your help!!!!!

---

### Post by Pumalite on 2007-09-13
You are welcome. Good luck.

---

