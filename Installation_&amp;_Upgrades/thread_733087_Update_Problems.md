---
title: "Update Problems"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by chazaw on 2008-03-23
I have been unable to start the update manager, if I click on it nothing happens. Any help would be appreciated

also tried sudo apt-get upgrade and got this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/915kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 28, in <module>
    import apt_pkg
ImportError: No module named apt_pkg
(Reading database ... 247099 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.81.2 (using .../update-manager-core_1%3a0.81.2_i386.deb) ...
'import site' failed; use -v for traceback
MemoryError
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
MemoryError
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.81.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
MemoryError
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace update-manager 1:0.81.2 (using .../update-manager_1%3a0.81.2_all.deb) ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
MemoryError
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
MemoryError
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.81.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
MemoryError
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager-core_1%3a0.81.2_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.81.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bapoumba on 2008-03-23
Could you please post your sources.list?
```
cat /etc/apt/sources.list
```
[Gutsy's update-manager-core is 1:0.81]("http://packages.ubuntu.com/update-manager-core"), not sure where you are getting this upgrade from..

---

### Post by chazaw on 2008-03-23
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe restricted main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe restricted main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties
deb [http://users.fulladsl.be/spb1804/](http://users.fulladsl.be/spb1804/) gutsy-printing bugtriage

---

### Post by bapoumba on 2008-03-23
You have feisty repos along with gutsy repos. Your profile says you are running gutsy, so please comment all the feisty repositories (or untick them from synaptic) + the last one (deb [http://users.fulladsl.be/spb1804/](http://users.fulladsl.be/spb1804/) gutsy-printing bugtriage) just for now. You will add back the third party repo after everything is working again.
You should end up with these repos (from my own sources.list so you can compare):
```
# Base.
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

# Bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

# Security.
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
```

Run:
```
sudp apt-get update
sudo apt-get dist-upgrade
```
and please post the output.

---

### Post by chazaw on 2008-03-23
No luck, also when I tried to update through synaptic repositories I get the message 

> *The repository information has changed. You have to click on the "Reload" button for your changes to take effect*

but when I reload and try to change again I get the same message.



**sudp apt-get update**

'import site' failed; use -v for traceback
MemoryError


**sudo apt-get dist-upgrade**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/915kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 28, in <module>
    import apt_pkg
ImportError: No module named apt_pkg
(Reading database ... 247099 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.81.2 (using .../update-manager-core_1%3a0.81.2_i386.deb) ...
'import site' failed; use -v for traceback
MemoryError
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
MemoryError
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.81.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
MemoryError
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace update-manager 1:0.81.2 (using .../update-manager_1%3a0.81.2_all.deb) ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
MemoryError
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
MemoryError
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.81.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
MemoryError
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager-core_1%3a0.81.2_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.81.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kevbert on 2008-03-23
Please try sudo apt-get install -f
to fix installed damaged packages.
Also, have you checked your PC memory recently ?

---

### Post by bapoumba on 2008-03-23
In addition to Kevbert'post, would you be running out of space on /var ?
```
df -H
```

And please post your modified sources.list + the outpout of the following:

```
apt-cache policy update-manager-core
```

---

### Post by chazaw on 2008-03-25
Update

Couple of things - 
Memory test was the first thing I did... OK
Plenty of space in /var

Looked in logs to find out exactly when this happened and found out it was a failed python 2.5 update.

Then I found this bug report
[https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/192992]("https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/192992")

I've been trying to fix with some of these suggestions.

Still trying

---

