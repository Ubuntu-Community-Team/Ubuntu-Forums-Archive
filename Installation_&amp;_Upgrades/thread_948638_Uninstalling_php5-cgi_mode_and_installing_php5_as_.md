---
title: "Uninstalling php5-cgi mode and installing php5 as an apache module"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by Landon6544 on 2008-10-15
I'm using Ubuntu Fiesty and need to install php5 as a module, instead of in CGI mode, how it's currently working. I have root access to the server, but I'm not the one who installed php5 in the first place. I need to uninstall php and reinstall it. Other instructions I have found on the net seem to be for other setups. Can anyone help me do this?

Thank you.

---

### Post by penguinpi.com on 2008-10-16
See if php5-cgi was installed with dpkg

~# dpkg -l |grep php5-cgi

if you see a result then do this:

~# dpkg --purge php5-cgi

and then install php5 apache module

~# apt-get install libapache2-mod-php5

~# a2enmod php5

---

### Post by Landon6544 on 2008-10-17
I did what you have said, and it says that php5-cgi isn't installed anymore, and that the php5 mod is already enabled. I have a php script called phpinfo that I ran to try and figure out the current php setup and it tells me version 5.2.6 is installed and that the gateway interface is CGI.

---

