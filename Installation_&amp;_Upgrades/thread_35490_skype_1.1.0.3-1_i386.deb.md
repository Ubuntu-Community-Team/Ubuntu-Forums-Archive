---
title: "skype_1.1.0.3-1_i386.deb"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by boosted on 2005-05-19
i got skype_1.1.0.3-1_i386.deb from [www.skype.com](www.skype.com).  I then used the command
 dpkg -i skype_1.1.0.3-1_i386.deb  

and got this:

Selecting previously deselected package skype.
(Reading database ... 63768 files and directories currently installed.)
Unpacking skype (from skype_1.1.0.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on dbus-1 (>= 0.23); however:
  Version of dbus-1 on system is 0.22-1ubuntu2.
 skype depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

so...  I did this:
apt-get install libqt3c102-mt
and got this:
Reading Package Lists... Done
Building Dependency Tree... Done
libqt3c102-mt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

the tried :
pt-get install dbus-1
Reading Package Lists... Done
Building Dependency Tree... Done
dbus-1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

i also tried to do it through Synaptic Package Manager and it said I had the newest ver of both but they are older than the req ver for the ones req by skype?  I am confused and New to Linux!!!!!

---

### Post by jasmuz on 2005-05-19
[QUOTE=boosted]i got skype_1.1.0.3-1_i386.deb from [www.skype.com](www.skype.com).  I then used the command
 dpkg -i skype_1.1.0.3-1_i386.deb  

and got this:

Selecting previously deselected package skype.
(Reading database ... 63768 files and directories currently installed.)
Unpacking skype (from skype_1.1.0.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on dbus-1 (>= 0.23); however:
  Version of dbus-1 on system is 0.22-1ubuntu2.
 skype depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

so...  I did this:
apt-get install libqt3c102-mt
and got this:
Reading Package Lists... Done
Building Dependency Tree... Done
libqt3c102-mt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

the tried :
pt-get install dbus-1
Reading Package Lists... Done
Building Dependency Tree... Done
dbus-1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

i also tried to do it through Synaptic Package Manager and it said I had the newest ver of both but they are older than the req ver for the ones req by skype?  I am confused and New to Linux!!!!![/QUOTE]
 Do this on the terminal, and tell me if it works for you, as it did for me...it will resolve the dependencies:

#sudo apt-get -f install

---

### Post by boosted on 2005-05-19
[QUOTE=jasmuz]Do this on the terminal, and tell me if it works for you, as it did for me...it will resolve the dependencies:

#sudo apt-get -f install[/QUOTE]

Ok.. this is what I got:

Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 92 not upgraded.

so is that what it is sup to do?  what do I do now?

---

### Post by ZeroA4 on 2005-05-23
[QUOTE=boosted]i got skype_1.1.0.3-1_i386.deb from [www.skype.com](www.skype.com).  I then used the command
 dpkg -i skype_1.1.0.3-1_i386.deb  

and got this:

Selecting previously deselected package skype.
(Reading database ... 63768 files and directories currently installed.)
Unpacking skype (from skype_1.1.0.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on dbus-1 (>= 0.23); however:
  Version of dbus-1 on system is 0.22-1ubuntu2.
 skype depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

so...  I did this:
apt-get install libqt3c102-mt
and got this:
Reading Package Lists... Done
Building Dependency Tree... Done
libqt3c102-mt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

the tried :
pt-get install dbus-1
Reading Package Lists... Done
Building Dependency Tree... Done
dbus-1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

i also tried to do it through Synaptic Package Manager and it said I had the newest ver of both but they are older than the req ver for the ones req by skype?  I am confused and New to Linux!!!!![/QUOTE]
You can follow this [http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype), they have a link to a modified .deb that refers to the libs in Ubuntu repos.

---

