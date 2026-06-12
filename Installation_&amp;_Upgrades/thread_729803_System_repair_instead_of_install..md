---
title: "System repair instead of install."
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by paulnewby on 2008-03-20
System repair instead of install.

I have tried all week to find the resolution to my system problems with no luck, even after posting 4-5 posts.

So i have decided to reinstall Ubuntu. Before i do this is there away to do any sort of 'repair' install etc so that i can just re-install the O/S to repair mine, whith out wipin guot my applications and other settings etc on my system?

as i have done quite a bit of customisation ect over the past 4\5 months since my initial install.

I am generally happy with the OS but have encounted a wide number of problems etc, mainly i think caused by updates, which has caused my latest suumingly un fixable problem.

with many things such as, update manager, install\remove application, text editor, software sources not working.

this has been driving me nuts ;-(

---

### Post by keratos on 2008-03-20
but WHAT IS your specific problem.

list them so we can deal with them

If there are too numerous a list of problems, or you find it difficult to articulate individual problems, then reinstal and only ever upgrade what is not working - good rule of thumb is if it works, dont change it!

---

### Post by paulnewby on 2008-03-20
I have been having on going problems with updates not working and not being able to use the add/remove programs, and a few other applications are not working text editor etc!

I have tried to edit my source list but its read only, is there away i can change it so i can edit the lines?

also i think my folder for dpkg is missing also


Hi there, i have tried what has been suggested with still no luck ;-(

when i tried sudo dpkg --configure -a this is what i get!

Setting up update-manager (1:0.81) ...
Traceback (most recent call last):
File "/usr/sbin/gconf-schemas", line 8, in <module>
import sys,os,os.path,shutil,tempfile
ImportError: No module named shutil
Error in sys.excepthook:
Traceback (most recent call last):
File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
from apport.fileutils import likely_packaged
File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
from apport.report import Report
File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ImportError: No module named urllib

Original exception was:
Traceback (most recent call last):
File "/usr/sbin/gconf-schemas", line 8, in <module>
import sys,os,os.path,shutil,tempfile
ImportError: No module named shutil
dpkg: error processing update-manager (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
update-notifier depends on update-manager; however:
Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
update-manager
update-notifier

****this is the out put when i type in : cat /etc/apt/sources.list***

paul@paul-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

I have also tried sudo apt-get install -f and other commands

in apt update etc with no success

---

### Post by oldos2er on 2008-03-20
Your sources.list looks ok; you may want to comment out the "deb cdrom" line. To edit this file you need to give yourself admin privileges, so type "gksudo gedit /etc/apt/sources.list" in a terminal to do that. If gedit isn't working for you, try "sudo nano /etc/apt/sources.list"

---

### Post by erginemr on 2008-03-20
Looking at the error messages issued, I also think that your system has been broken badly. So, although I appreciate oldos2er's efforts to fix your system, I have to suggest you to stick to your original plan and but do a clean reinstall.

You can save most of your customization by transfering your /home folder to a new partition. The following guide will be helpful: 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

The proper size of /home depends on the available space of your hard drive, but I'd say, 10-15 GB is more than enough for your root system (/) and the rest is for swap and /home.

If you succeed in creating a separate /home partition and transfer all your personal setings there, you will have saved almost all your personal customizations. Then, all you need to do is to take note of the new applications you have installed and reinstall them as well after you reinstall Ubuntu. Just make sure to indicate the mount point your /home partition correctly as /home, but not to format it during the install.

So, in short, pack up all you can and do a clean reinstall. I also suggest you to backup your /etc folder to a tar.gz archive in your home folder in case you may need to restore some system-wide settings from there in your new install.

---

### Post by keratos on 2008-03-20
> **oldos2er said:**
> Your sources.list looks ok; you may want to comment out the "deb cdrom" line. To edit this file you need to give yourself admin privileges, so type "gksudo gedit /etc/apt/sources.list" in a terminal to do that. If gedit isn't working for you, try "sudo nano /etc/apt/sources.list"

This isn't going to make the slightest bit of difference.

see below

---

### Post by keratos on 2008-03-20
> **erginemr said:**
> Looking at the error messages issued, I also think that your system has been broken badly. So, although I appreciate oldos2er's efforts to fix your system, I have to suggest you to stick to your original plan and but do a clean reinstall.

You can save most of your customization by transfering your /home folder to a new partition. The following guide will be helpful: 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

The proper size of /home depends on the available space of your hard drive, but I'd say, 10-15 GB is more than enough for your root system (/) and the rest is for swap and /home.

If you succeed in creating a separate /home partition and transfer all your personal setings there, you will have saved almost all your personal customizations. Then, all you need to do is to take note of the new applications you have installed and reinstall them as well after you reinstall Ubuntu. Just make sure to indicate the mount point your /home partition correctly as /home, but not to format it during the install.

So, in short, pack up all you can and do a clean reinstall. I also suggest you to backup your /etc folder to a tar.gz archive in your home folder in case you may need to restore some system-wide settings from there in your new install.


Agreed.

Did you interrupt an install or inadvertently restart X or your machine, or stop a apt-get upgrade or install, or did you attempt to install an experimental package??

The reason I ask is this line..

```
subprocess post-installation script returned error exit status 1
```

A non-zero exit code is an error! 

post-install did not complete.

No need to reinstall I think...follow this guide, worked for me some time ago when my machine crashed .. although that was due to my foobared kernel compile that went wrong!!

```
http://www.debianhelp.co.uk/debianproblem.htm
```

---

### Post by paulnewby on 2008-03-21
Thanks for the advice, 

I will try all that has been suggested then post back the results.

The initial problems started when the system crashed during a updtes install.i assume that is the cause of it.

also i have lost the DPKG folder for some reason?

---

### Post by forestpixie on 2008-03-21
I would say yes  that's the cause of the problems. If you do have to resort to a reinstall - firstly - look into the seperate /home.

Also - you say you've customised - if you know what you've customised - keep copies of the files and then assuming that the install is in the same state use the backed up customised files again

eg if you've mucked about with xorg.conf, make a copy to a flash drive and then once the system has all the drivers necessary you can copy xorg back. I did the same.

---

### Post by keratos on 2008-03-21
> **forestpixie said:**
> I would say yes  that's the cause of the problems. If you do have to resort to a reinstall - firstly - look into the seperate /home.

Also - you say you've customised - if you know what you've customised - keep copies of the files and then assuming that the install is in the same state use the backed up customised files again

eg if you've mucked about with xorg.conf, make a copy to a flash drive and then once the system has all the drivers necessary you can copy xorg back. I did the same.

Concur with this most wise advice ;-)

---

