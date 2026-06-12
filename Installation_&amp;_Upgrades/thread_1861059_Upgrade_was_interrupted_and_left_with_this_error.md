---
title: "Upgrade was interrupted and left with this error"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by awam66 on 2011-10-15
I have a friend who left his computer (Dell Studio 1555) overnight to upgrade to 11.10 but in the morning faced with a blank screen he switched it off. 
I have done a "sudo dpkg -a --reconfigure" and a "sudo apt-get install -f" which has allowed us to get back a working system, however during the latter I get the following.

> Setting up dictionaries-common (1.11.5ubuntu1) ...
update-default-ispell: Question empty but elements installed for class "ispell"
dictionaries-common/default-ispell: return code: "0", value: ""
Choices: , Manual symlink setting
shared/packages-ispell: return code: "10" owners/error: "shared/packages-ispell doesn't exist"
Installed elements: american (American English)

Please see "/usr/share/doc/dictionaries-common/README.problems", section
"Debconf database corruption" for recovery info.

update-default-ispell: Selected ispell dictionary "" 
does not correspond to any installed package in the system
and no alternative ispell dictionary could be selected.
dpkg: error processing dictionaries-common (--configure):
subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of myspell-en-za:
myspell-en-za depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
Package dictionaries-common is not configured yet.
Package openoffice.org-updatedicts is not installed.
Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing myspell-en-za (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ienglish-common:
ienglish-common depends on dictionaries-common (>= 1.10.6~); however:
Package dictionaries-common is not configured yet.
dpkg: error processing ienglish-common (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of iamerican:
iamerican depends on dictionaries-common; however:
Package dictionaries-common is not configured yet.
iamerican depends on ienglish-common (= 3.3.02-5); however:
Package ienglish-common is not configured yet.
dpkg: error processing iamerican (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ispell:
ispell depends on dictionaries-common; however:
Package dictionaries-common is not configured yet.
dpkg: error processing ispell (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hunspell-en-ca:
hunspell-en-ca depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
Package dictionaries-common is not configured yet.
Package openoffice.org-updatedicts is not installed.
Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing hunspell-en-ca (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-au:
myspell-en-au depends on dictionaries-common (>= 1.0); however:
Package dictionaries-common is not configured yet.
dpkg: error processing myspell-en-au (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-gb:
myspell-en-gb depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
Package dictionaries-common is not configured yet.
Package openoffice.org-updatedicts is not installed.
Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing myspell-en-gb (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hunspell-en-us:
hunspell-en-us depends on dictionaries-common (>= 0.10); however:
Package dictionaries-common is not configured yet.
dpkg: error processing hunspell-en-us (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aspell-en:
aspell-en depends on dictionaries-common (>= 0.49.2); however:
Package dictionaries-common is not configured yet.
dpkg: error processing aspell-en (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythes-en-us:
mythes-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
Package dictionaries-common is not configured yet.
Package openoffice.org-updatedicts is not installed.
Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing mythes-en-us (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
dictionaries-common
myspell-en-za
ienglish-common
iamerican
ispell
hunspell-en-ca
myspell-en-au
myspell-en-gb
hunspell-en-us
aspell-en
mythes-en-us
 
Can anyone help please??

---

### Post by awam66 on 2011-10-16
Any one any ideas on this please? I know of at least one other person with this problem!

---

### Post by skakri on 2011-10-18
I get very similar error on eclipse installation - [http://pastebin.com/HdjdpnzQ](http://pastebin.com/HdjdpnzQ) . Dist upgrade was full with errors as well (dpkg errors, GdkPixbugf errors, etc).

---

### Post by searchfgold6789 on 2011-10-18
I usually use ```
dpkg --configure -a
```

---

### Post by spud1 on 2012-05-02
i had a same problem and someone gave me this and it fix it........   let me know if it helps


[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

