---
title: "[SOLVED] Wicd Install Problems"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by rhololkeolke on 2008-10-02
I'm using 8.04 and I upgraded wicd through synaptic.  When it came up it asked if I wanted to keep my old scripts and thinking it meant my config files I clicked yes.  Then I got a problem.  When I rebooted my computer it said that wicd had crashed.  I tried restarting it but that didn't work so I decided I would just uninstall and then reinstall.  When I went to uninstall it didn't work.  I found this thread [http://wicd.net/punbb/viewtopic.php?id=187](http://wicd.net/punbb/viewtopic.php?id=187) and it said to delete the wicd.prerm script.  I did and I was able to uninstall it.  I then proceeded to reinstall it but when I go to reinstall it either from the repository or from a deb file it says the following:
```
Selecting previously deselected package wicd.
(Reading database ... 211965 files and directories currently installed.)
Unpacking wicd (from .../Desktop/wicd_1.5.3_all.deb) ...
Setting up wicd (1.5.3) ...
ls: cannot access /opt/wicd/encryption/configurations/: No such file or directory
```
I don't see how there could be a directory there considering I purged the package.  I need to know how to reinstall wicd.  Is there a way to force it to install the package and ignore whether it can find it or not?  All help is appreciated thanks.

---

### Post by imdano on 2008-10-02
Create a /opt/wicd/encryption/configurations directory with nothing in it.  It should install correctly then.  See this thread for more info: [http://wicd.net/punbb/viewtopic.php?pid=865](http://wicd.net/punbb/viewtopic.php?pid=865)

---

### Post by rhololkeolke on 2008-10-03
I did what that form said and I don't get an error when it installs; however, it also doesn't seem like it is actually installing.  When I try to start the tray icon and the gui using the command either 
```
/opt/wicd/tray.py
``` 
or
```
/opt/wicd/gui.py
```
It says that it cannot be found.  I went to the folder /opt/wicd and the only thing there is the encryption folder that I made like that form instructed.  I even tried temporarily changing the permissions so that I could write to it without super user access.

---

### Post by rhololkeolke on 2008-10-03
Never mind it did install correctly they just moved the frontend to /usr/bin so in order to start the tray icon I have to type 
```
/usr/bin/wicd-client
```.

---

### Post by imdano on 2008-10-03
Just "wicd-client" would work as well.

---

