---
title: "Kontact won't start: Akonadi problem on Lucid"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by jynyl on 2010-05-01
Fresh install of Kubuntu 10.04 AMD64.
On first startup, Kontact worked, but I had to manually start Akonadi (from system tray) to get contacts to work.
After reboot, Kontact won't start, instead showing a red box with an X, and "Akondaki not operational".  
The box on the screen (selftest) says "MySQL server log contains errors", and "Akonadi server process not registered at D-Bus".
The report is saves says Test 14: error "no resource agents found".
If I close the Akonadi window, and try to start Akonadi from the system tray, it gives the same errors.

Any hints on how to fix AKonadi?
Or, is this not ready for prime time yet? (and how can I remove it?)

---

### Post by khamil8686 on 2010-05-01
seconded :) i tried to start akonadi from the system tray but it wont start, says...
MySQL log contains errors
Akonadi server process not registered at dbus
no resource agents found
previous akonadi error found
current akonadi error found
previous akonadi error found

The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system

ill post if i find a solution in my googling :)

---

### Post by jynyl on 2010-05-01
Kontact (kmail and Contacts) is going now, but I don't know why.  After a reboot, it started to work.
Seems like Akonadi is a bit flakey.

---

### Post by charles.figura on 2010-05-02
I've been having problems with akonadi and kontact as well, and they sound like the same ones.  When I did a clean install of 10.04, I've tried to work with it, migrate address books, the rest.  Kontact always starts up, but the 'Contacts' (address book) tab is usually greyed out, and the error report says that no resource agents are found.

I've found that if I use 'akonadiconsole' and restart akonadi, it will take care of the problem.  The addressbook tab becomes active (without restarting kontact).

Since I'm not actually *changing* anything when I restart akonadi, it seems that akonadi may be buggy - not ready for primetime.

---

### Post by jynyl on 2010-05-02
Now it is not working again.  Kontact won't start at all, after a reboot.  No error messages, but I suspect Akonadi.

---

### Post by jynyl on 2010-05-02
Appears to relate to this bug on launchpad ...
[https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/554514](https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/554514)

---

