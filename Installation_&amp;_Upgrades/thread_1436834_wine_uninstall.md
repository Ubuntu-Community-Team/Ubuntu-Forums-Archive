---
title: "wine uninstall"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by amite on 2010-03-23
i am basically a windows user and recently i switched to linux(ubuntu).i hv installed wine installation of windows based s/w.i installed "Pacemaster uml diagrammer" it was a trial pack and after a month when i tried to uninstall it,nothing happened.

finally i did 
amitesh@ami:~$ sudo dpkg -P wine1.2
(Reading database ... 198377 files and directories currently installed.)
Removing wine1.2 ...
Purging configuration files for wine1.2 ...
amitesh@ami:~

But yet wine is available in Application and in it uml diagrammer(other application has removed).

what to do?help!

---

### Post by tom4everitt on 2010-03-23
A more standard solution for removing wine would have been:

sudo apt-get remove --purge wine1.2

perhaps that would work better. If it doesn't work directly, you might need to install wine (again) before you remove it this way.


EDIT: To install wine again, just run: sudo apt-get install wine1.2

---

### Post by Gregorybekkers on 2010-03-23
Or go just to the Ubuntu software center and remove it from installed programs.

---

### Post by amite on 2010-03-23
it's not working.....i tried
sudo apt-get remove --purge wine1.2 and result is.

amitesh@ami:~$ sudo apt-get remove --purge wine1.2
[sudo] password for amitesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine1.2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  ttf-tahoma-replacement ttf-symbol-replacement libmpg123-0 winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

BUT IT didn't work too...............


After that reinstalled wine1.2 and first try to uninstall "pacemaster uml" but gave linstall.log isn't available.
So again i uninstall wine with folowing code
$ sudo apt-get remove --purge wine1.2

And again it didn't work ....................

---

### Post by tom4everitt on 2010-03-23
Okay, then you could just remove it manually:

Go to Preferences->Main Menu. Click on Applications and uncheck wine. Then it will no longer be displayed in your applications menu.


(The package is already removed, so all that is left is the menu entry.)

---

