---
title: "brother bloody printer killed synaptic"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by klemencic on 2008-05-04
I have attempted to install the cupswrapper package for a Brother MFC5860CN printer from the Brother website
during the installation it come up with an exit error message and now I can not use Synaptic, Add/Remove or dpkg
When I try to to start Synaptic I receive the following

E: The package mfc5860cncupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Add/Remove gives me
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I ran apt-get update and then with apt-get install -f I receive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc5860cncupswrapper needs to be reinstalled, but I can't find an archive for it.


I have also tried to remove the package with dpkg and received the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc5860cncupswrapper needs to be reinstalled, but I can't find an archive for it.

My Ubuntu is 8.04

Thanks for any help

---

### Post by PmDematagoda on 2008-05-04
Can you post the outputs of:-
```
dpkg -C
```
and
```
cat /etc/apt/sources.list
```

---

### Post by klemencic on 2008-05-05
outputs are as follows


klem@klem-linux:~$ dpkg -C
The following packages are in a mess due to serious problems during
installation. They must be reinstalled for them (and any packages
that depend on them) to function properly:
 mfc5860cncupswrapper Brother CUPS Inkjet Printer Definitions


klem@klem-linux:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
klem@klem-linux:~$

---

### Post by PmDematagoda on 2008-05-05
Remove the package with:-
```
sudo apt-get remove --purge mfc5860cncupswrapper
```

Then download the package again and try and install it. Also you may have better luck if you get the drivers directly from the Ubuntu repositories, you can search for the Brother printer drivers from [Ubuntu Packages]("http://packages.ubuntu.com/").

---

### Post by klemencic on 2008-05-05
> **PmDematagoda said:**
> Remove the package with:-
```
sudo apt-get remove --purge mfc5860cncupswrapper
```

Then download the package again and try and install it. Also you may have better luck if you get the drivers directly from the Ubuntu repositories, you can search for the Brother printer drivers from [Ubuntu Packages]("http://packages.ubuntu.com/").

I have tried this but receive the following message and the problem remains

klem@klem-linux:~$ sudo apt-get remove --purge mfc5860cncupswrapper
[sudo] password for klem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc5860cncupswrapper needs to be reinstalled, but I can't find an archive for it.

---

### Post by PmDematagoda on 2008-05-06
Then try removing the package with:-
```
sudo dpkg -P --force-remove-reinstreq mfc5860cncupswrapper
```

---

### Post by klemencic on 2008-05-06
> **PmDematagoda said:**
> Then try removing the package with:-
```
sudo dpkg -P --force-remove-reinstreq mfc5860cncupswrapper
```

Here is the output of the last command, at least now it says what files it cannot find

klem@klem-linux:~$ sudo dpkg -P --force-remove-reinstreq mfc5860cncupswrapper
[sudo] password for klem: 
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 111900 files and directories currently installed.)
Removing mfc5860cncupswrapper ...
/var/lib/dpkg/info/mfc5860cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc5860cn/cupswrapper/cupswrappermfc5860cn: not found
dpkg: error processing mfc5860cncupswrapper (--purge):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc5860cncupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc5860cn/cupswrapper/cupswrappermfc5860cn: not found
chmod: cannot access `/usr/local/Brother/Printer/mfc5860cn/cupswrapper': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc5860cncupswrapper

---

