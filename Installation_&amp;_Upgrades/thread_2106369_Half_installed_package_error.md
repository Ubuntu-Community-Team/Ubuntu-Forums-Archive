---
title: "Half installed package error"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by mckaymotoworks on 2013-01-18
I attempted to install DraftSight via .deb package in 12.10 after the dependencies were met. 
Received the following error when attempting to install from Terminal: 
[B]Selecting previously unselected package dassault-systemes-draftsight.
(Reading database … 211618 files and directories currently installed.)
Unpacking dassault-systemes-draftsight (from …/Downloads/draftSight.deb) …
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host[/B]

Now receiving system error notification that it's half installed and causing the error. 
It's crashing the Software Center, I cannot figure out how to kill the offending dpkg or how to install what is installed to start over.

EDIT: [B]sudo apt-get remove dassult-systemes-draftsight
[sudo] password for user: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[/B]Made a bit more progress:[B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package dassault-systemes-draftsight needs to be reinstalled, but I can't find an archive for it.

[/B]dpkg/Status[B]:
Package: dassault-systemes-draftsight
Status: install reinstreq half-installed
Priority: extra
Section: applications
Architecture: i386
Version: 2012.7.347
[/B]

---

### Post by mckaymotoworks on 2013-01-18
Says it's not installed:[B]
user:~$ sudo dpkg --force-remove-reinstreq --remove  dassult-systemes-draftsight
dpkg: warning: ignoring request to remove dassult-systemes-draftsight which isn't installed
user@computer:~$ sudo dpkg -e DraftSight
dpkg-deb: error: failed to read archive `DraftSight': No such file or directory
[/B]

---

### Post by mckaymotoworks on 2013-01-19
Added a few screen shots, odd the Terminal says the software is not installed, but the Status file clearly shows it half installed as does the Crash log.

---

### Post by mckaymotoworks on 2013-01-19
Can anyone help? Did I post in the wrong section? My system is unable to update until this is resolved.

---

### Post by mckaymotoworks on 2013-01-21
Can some one please point me to another board etc where I can possibly get this answered? I've tried to be patient waiting at least in 12hr or 24 increments before bumping.

---

### Post by steeldriver on 2013-01-21
are you sure it's not just a simple typo?

> **mckaymotoworks said:**
> dpkg/Status[B]:
Package: dass[COLOR=Red]au[/COLOR]lt-systemes-draftsight
Status: install reinstreq half-installed
Priority: extra
Section: applications
Architecture: i386
Version: 2012.7.347
[/B]

> **mckaymotoworks said:**
> Says it's not installed:[B]
user:~$ sudo dpkg --force-remove-reinstreq --remove  dass[COLOR=Red]u[/COLOR]lt-systemes-draftsight
dpkg: warning: ignoring request to remove dass[COLOR=Red]u[/COLOR]lt-systemes-draftsight which isn't installed
[/B]

---

### Post by mckaymotoworks on 2013-01-21
Thank you for pointing that out, quite embarrassing, it was indeed a typo.  
Always the simple things..... :D

---

### Post by steeldriver on 2013-01-21
sometimes it just need a fresh set of eyes ):P

---

