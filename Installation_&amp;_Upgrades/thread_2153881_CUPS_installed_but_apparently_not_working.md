---
title: "CUPS installed but apparently not working"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2013-06-12
I finally got around to installing Lubuntu 13.04 on my ASUS so now I am triple booting with 12.04 and 12.10.  Today I decided that I might want to print something so I downloaded and tried to install HPLIP.  Got the following error.
 
> error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

What gives.  Apparently I have it installed but it is not recognized?  Is there a work around available?

---

### Post by monkeybrain2012 on 2013-06-12
Hi, 

I have run into a similar problem. I grab the deb from Precise's repository and it worked. I have filed a bug report, if that is your problem please go there and add an affect me too.
[URL="http://ubuntuforums.org/showthread.php?t=2150773"]
http://ubuntuforums.org/showthread.php?t=2150773[/URL]

---

### Post by Rex Bouwense on 2013-06-12
OK.  I added "this affects me" to the Launchpad bug.  What does cups-pdf have to do with the system telling me that cups is not installed?

---

### Post by monkeybrain2012 on 2013-06-12
Ok, on second reading It appears to be a different problem then, I don't have problem installing cups or cups-pdf, just that cups-pdf is installed but system doesn't detect it. Maybe it is related.

---

### Post by Rex Bouwense on 2013-06-12
I have the newest version of cups installed already.  Apparently, it is not being recognized as being installed or at least that is what HPLIP says when I try to install it.  Also no printers are discovered.  Nice.

---

### Post by Rex Bouwense on 2013-06-12
OK, for those of you that are interested,  I uninstalled CUPS and reinstalled it.  Then I configured the printer before I tried to install HPLIP 3.13.5.  When I tried to install HPLIP this time it recognized CUPS and installed.  I do not know what the problem was, but now I have a functional printer in Lubuntu 13.04.

---

