---
title: "upgrade from 13.04 to 13.10 didn't complete now won't boot"
date: 2013-12-20
forum: Installation &amp; Upgrades
---

### Post by julchad46 on 2013-12-20
Trying to upgrade from 13.04 to 13.10 it didn,t  complete. Now pc boots to root command. What can I input to restore?

---

### Post by Bashing-om on 2013-12-20
julchad46; Hi !

Ouch, Try:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade

```

[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by julchad46 on 2013-12-20
Tried all options. Last line 
Dpkg was interrupted,  you must manually run ' sudo dpkg --configure a' to correct the problem. When I put this in it comes up with ' dpkg: error: unable to access dpkg status area: Read only file system' Any suggestions what should do now?

---

### Post by Bashing-om on 2013-12-20
julchad46; Hey.

" error: unable to access dpkg status area: Read only file system'" ; Puts me in mind that you are booting through the recovery console to a root login.
If this is so .. then the file system is not at that time mounted read/write. To remount the file system read/write :
```

mount -o remount,rw /

```
And try my last command sequence once more and see what results.

There is hope to (re)build the file system yet.

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by julchad46 on 2013-12-21
It was  indeed the case entered you suggested command and it then put into state where it would carry out suggested command sequence. It has now brought me back to a root comand . What next?

---

### Post by julchad46 on 2013-12-21
ignore my last sentance in last post. Just rebooted and the system started up OK. Thanks for your clear help Bashing-Om. Much appreciated.

---

### Post by Bashing-om on 2013-12-21
julchad46; Great !

Glad to be of some small assistance.
Please mark this thread as solved, aids others seeking a solution, and helps keep the forum tidy.

This is open source at it's best ->

[INDENT][INDENT]all of one and 1 for all
[/INDENT][/INDENT]

---

