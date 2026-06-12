---
title: "Add/Remove applications failure"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by lenwftm on 2008-01-05
I have newly installed Ubuntu 7.10 on a Dell Latitude 600 laptop, and managed to get the Broadcom wireless working with ndiswrapper. However, Synaptic package manager reports that ndiswrapper-utils-1.9 is broken. I removed it and tried to re-install it (along with ndiswrapper-common) but got the message:

E: /cdrom//pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb: trying to overwrite `/sbin/loadndisdriver', which is also in package ndiswrapper

Also, Applications - Add/Remove resulted in:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I ran the update and install commands without error, but it made no difference.

How can I tackle this problem??

---

### Post by taurus on 2008-01-05
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Sef on 2008-01-05
> check the file permissions and correctness of the file /etc/apt/sources.list

If you haven't checked, please do and post the results here.

Applications > Accessories > Terminal

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by lenwftm on 2008-01-05
Thanks, the permissions were all read-only, and here's the output:

len@lenubu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
len@lenubu:~$

---

### Post by taurus on 2008-01-05
You have limited repos available for you in /etc/apt/sources.list.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  Then, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by lenwftm on 2008-01-05
Ok, sudo apt-get update ran, but ended with:

Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Fetched 7377kB in 4m0s (30.7kB/s)                        
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2)  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
len@lenubu:~$ 

**Then:**

len@lenubu:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
len@lenubu:~$ 

**???**

---

### Post by lenwftm on 2008-01-05
OK, I ran update a couple more times, finally successfully, and then ran sudo aptget upgade with the following result:

len@lenubu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ndiswrapper-utils-1.9: Depends: ndiswrapper-common but it is not installed
E: Unmet dependencies. Try using -f.
len@lenubu:~$ 

I then ran Synaptic package manager to reinstall, ndiswrapper-utils-1.9 but still get the error message:

E: /var/cache/apt/archives/ndiswrapper-common_1.43-1ubuntu2_all.deb: trying to overwrite `/sbin/loadndisdriver', which is also in package ndiswrapper

---

### Post by taurus on 2008-01-05
```
sudo apt-get -f install
```
Close down synaptic first before you run that command.

---

### Post by lenwftm on 2008-01-05
Closed Synaptic and and ran sudo apt-get -f install, which output:

len@lenubu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 150 not upgraded.
1 not fully installed or removed.
Need to get 0B/19.2kB of archives.
After unpacking 106kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 89016 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.43-1ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/ndiswrapper-common_1.43-1ubuntu2_all.deb (--unpack):
 trying to overwrite `/sbin/loadndisdriver', which is also in package ndiswrapper
Errors were encountered while processing:
 /var/cache/apt/archives/ndiswrapper-common_1.43-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
len@lenubu:~$

---

### Post by lenwftm on 2008-01-05
OK, Problem solved. There must have been an incorrect version of ndiswrapper installed.

Uninstalling completely and re-installing ndiswrapper appears to have cleared the problem.

Thanks for your help.

---

### Post by SoDanishWasLike on 2008-01-05
I just installed Ubuntu 7.10 hours ago

I tried editing my sources.list, but I am told I don't have permission to save my changes. How do I get around this?

---

### Post by taurus on 2008-01-05
> **SoDanishWasLike said:**
> I just installed Ubuntu 7.10 hours ago

I tried editing my sources.list, but I am told I don't have permission to save my changes. How do I get around this?

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by SoDanishWasLike on 2008-01-05
Thank you Taurus, I think I forgot the gksudo part =)

---

