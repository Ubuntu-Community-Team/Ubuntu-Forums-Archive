---
title: "source list and update problems"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by paulnewby on 2008-03-18
Hi all, 

I have been having on going problems with updates not working and not being able to use the add/remove programs, and a few other applications are not working text editor etc!

I have tried to edit my source list but its read only, is there away i can change it so i can edit the lines?

Or could a do a re-insatll that will correct any incorrect or corrupt enterys etc?

Thanks in advance

---

### Post by PmDematagoda on 2008-03-18
Go to Software Sources in System>Administration>Software Sources and make the required changes. That should do the trick.

---

### Post by paulnewby on 2008-03-18
Thats the problem i also can't access Software Sources either!!!???

I am really unsure what i can try next?

:mad:

---

### Post by PmDematagoda on 2008-03-18
Post the output of:-
```
cat /etc/apt/sources.list
```
Also when did you start facing these problems? Is this a clean install of Ubuntu?

---

### Post by paulnewby on 2008-03-18
I have also tried cat /etc/apt/sources.list with no success.

the problems started after a recent update that i installed, which i think was on saturday!

they faild to install half way through.

---

### Post by PmDematagoda on 2008-03-18
> **paulnewby said:**
> they faild to install half way through.

The plot thickens.

Boot Ubuntu in Recovery Mode and then execute:-
```
sudo dpkg --configure -a
```
and 
```
sudo apt-get install -f
```
Then see if that fixes your problem.

---

### Post by paulnewby on 2008-03-18
Thanks for that, 

I am at work at the moment, but i will give it a try tonight...and post the results if it worked or not :confused:

---

### Post by paulnewby on 2008-03-18
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

Thanks again

---

### Post by PmDematagoda on 2008-03-18
That looks bad, did you try the other command I gave you?

---

### Post by paulnewby on 2008-03-19
Yes i tried both commands you gave me, which gave similar error messages ;-(

Do you think there is a way to fx it, or a re-install the only option...

Thanks for your help so far

---

### Post by PmDematagoda on 2008-03-19
> **paulnewby said:**
> Yes i tried both commands you gave me, which gave similar error messages ;-(

Do you think there is a way to fx it, or a re-install the only option...

Thanks for your help so far

Unfortunately I do not know if there is a way of fixing this problem. I suggest that you wait for sometime until someone replies and then, if someone hasn't replied, to reinstall the system.

---

### Post by paulnewby on 2008-03-19
Is a re-install simple to do, with out loosing to many applications. Will i just be able to reinstall whats on the operating system partition?

---

### Post by PmDematagoda on 2008-03-19
A reinstall is a reinstall, after you do a reinstall then all of your applications and data will be removed and replaced with the default when you install Ubuntu.

If you have any important files or data then make a backup of them before reinstalling Ubuntu on the same partition/drive.

---

### Post by paulnewby on 2008-03-20
Can any one tell me if there is a certain or best way to do a re-install, as my system is beond repair now i feel?

should i reinstall gusty 7.10 or go for the new 8.** version?

---

### Post by PmDematagoda on 2008-03-20
> **paulnewby said:**
> Can any one tell me if there is a certain or best way to do a re-install, as my system is beond repair now i feel?

should i reinstall gusty 7.10 or go for the new 8.** version?

It is highly recommended that you use Ubuntu 7.10 until Ubuntu 8.04 comes out since Ubuntu 8.04 is still in development and may cause problems for you.

---

