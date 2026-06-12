---
title: "Picasa_3.0-current_amd64.deb    -   Anyone?"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by bhawkes on 2012-10-12
Desperate for a copy of above. Is anyone able to share?

---

### Post by Lars Noodén on 2012-10-12
Picasa isn't really available for Linux.  It is a Windows application wrapped in WINE.  So you could just as well try running the plain Windows version under regular WINE instead.  The Picasa web page does not even offer the fake Linux version, so your only option is to try WINE if you really want Picasa.  

Or you might be better off with a native photo manager like Shotwell or Digikam.

---

### Post by oldfred on 2012-10-12
I just install wine and run the Windows version. No real issues that I can tell. I already have the MS fonts installed.

&#65279;sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine winetricks

Configure Wine to set up directory,  Applications, Wine, Configure

Then download picasa for windows
 ([http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe))
cd && wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)
Move it into .wine/drive_c/Program Files
wine picasa39-setup.exe

Somewhat related info, winetricks did not used to be in repository so any instructions to separately download are obsolete:
[http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html](http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html)
[http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)
[http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html)
But I never installed Picasa 3.0
[http://ubuntuforums.org/showthread.php?t=1385837](http://ubuntuforums.org/showthread.php?t=1385837)

---

### Post by megamania on 2012-10-13
I was looking for Picasa too and found both versions:

32bit
[http://tiny.cc/8j3alw](http://tiny.cc/8j3alw) 
64bit
[http://tiny.cc/al3alw](http://tiny.cc/al3alw)

Both links redirect to rapidshare.com.

---

