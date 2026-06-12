---
title: "Broken package - can't install anything"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by mr_si on 2011-09-09
I've got a broken package and I can't install anything.

si@shed:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  pips-snx110
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3,965kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 176071 files and directories currently installed.)
Removing pips-snx110 ...
dpkg: error processing pips-snx110 (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 pips-snx110
E: Sub-process /usr/bin/dpkg returned an error code (1)

si@shed:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
  pips-snx110: Depends: pips-common (>= 3.7.0) but it is not installable
               Depends: pips-debian4.0 (>= 3.7.0) but it is not installable
E: Unmet dependencies. Try using -f.

si@shed:~$ sudo dpkg --remove --force-all pips-snx110
(Reading database ... 176071 files and directories currently installed.)
Removing pips-snx110 ...
dpkg: error processing pips-snx110 (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 pips-snx110

Ub 10.04 


Can I fix it? Ta

---

### Post by Old_Grey_Wolf on 2011-09-09
Have you tried running ```
sudo apt-get -f install
``` a second time?

If you have, post the output from this command ```
sudo apt-get update
```

And then post the output from this command ```
sudo apt-get upgrade
```

---

### Post by mr_si on 2011-09-10
Thanks for looking :-)

```
si@shed:~$ sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release.gpg                        
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB          
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB      
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid-updates Release.gpg                
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release                            
Hit http://gb.archive.ubuntu.com lucid-updates Release               
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://gb.archive.ubuntu.com lucid/main Packages                 
Hit http://linux.dropbox.com lucid Release.gpg 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_GB    
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid/restricted Packages
Hit http://gb.archive.ubuntu.com lucid/main Sources
Hit http://gb.archive.ubuntu.com lucid/restricted Sources
Hit http://gb.archive.ubuntu.com lucid/universe Packages
Hit http://gb.archive.ubuntu.com lucid/universe Sources
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://gb.archive.ubuntu.com lucid-updates/main Packages
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com lucid-updates/main Sources
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com lucid-updates/universe Packages
Hit http://gb.archive.ubuntu.com lucid-updates/universe Sources
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://linux.dropbox.com lucid Release
Hit http://linux.dropbox.com lucid/main Packages
Reading package lists... Done

```
```
si@shed:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  pips-snx110: Depends: pips-common (>= 3.7.0) but it is not installable
               Depends: pips-debian4.0 (>= 3.7.0) but it is not installable
E: Unmet dependencies. Try using -f.

```

---

### Post by Old_Grey_Wolf on 2011-09-10
Post the output of this command ```
cat /etc/apt/sources.list
```

It looks like you may have a PPA or something in the sources.list for a printer driver that needs to be fixed. I think it is related to the Epson PIPS drivers.

Also post the output from this command ```
ls /etc/apt/sources.list.d
```

---

### Post by mr_si on 2011-09-10
```
si@shed:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

``````
si@shed:~$ ls /etc/apt/sources.list.d
dropbox.list

```

---

### Post by Old_Grey_Wolf on 2011-09-11
You will need to remove the Canon PIPS driver references.

Enter these commands
```
cd /var/lib/dpkg/info
```
```
sudo mv pips-snx110* /home/si/Desktop/pips
```
```
sudo apt-get -f install
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
If it works then you can remove the pips folder from your Desktop.

---

### Post by mr_si on 2011-09-11
:D

Thanks for taking the time out to sort this out for me, much appreciated.

---

### Post by Old_Grey_Wolf on 2011-09-11
I take it that it worked.

---

