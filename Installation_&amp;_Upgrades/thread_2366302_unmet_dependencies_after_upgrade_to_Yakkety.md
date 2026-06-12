---
title: "unmet dependencies after upgrade to Yakkety"
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2017-07-16
I upgraded a few days ago, now I'm getting messages that I have unmet dependencies:
Here is pertinent terminal output:

```
root@reuven-Ubuntu:/home/reuven# apt-get check
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gnome-session : Depends: gnome-session-bin (>= 3.20.2-1ubuntu7) but 3.18.1.2-1ubuntu1.16.04.2 is installed
                 Depends: gnome-session-common (= 3.20.2-1ubuntu7) but 3.18.1.2-1ubuntu1.16.04.2 is installed
 systemd : Depends: libsystemd0 (= 229-4ubuntu17) but 231-9ubuntu5 is installed
E: Unmet dependencies. Try using -f.
```

```
root@reuven-Ubuntu:/home/reuven# apt-get install --fix-broken && sudo apt-get autoremove && sudo apt-get update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  cgmanager
Use 'apt autoremove' to remove it.
The following additional packages will be installed:
  gnome-session-bin gnome-session-common indicator-session libpam-systemd systemd
  ubuntu-session upstart
Suggested packages:
  systemd-ui systemd-container graphviz upstart-monitor
Recommended packages:
  unity-control-center-signon | gnome-control-center-signon | mate-control-center
The following packages will be REMOVED:
  systemd-shim
The following packages will be upgraded:
  gnome-session-bin gnome-session-common indicator-session libpam-systemd systemd
  ubuntu-session upstart
7 upgraded, 0 newly installed, 1 to remove and 1776 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,031 kB of archives.
After this operation, 9,839 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 456544 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
root@reuven-Ubuntu:/home/reuven#apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  cgmanager
Use 'apt autoremove' to remove it.
The following additional packages will be installed:
  gnome-session-bin gnome-session-common indicator-session libpam-systemd systemd
  ubuntu-session upstart
Suggested packages:
  systemd-ui systemd-container graphviz upstart-monitor
Recommended packages:
  unity-control-center-signon | gnome-control-center-signon | mate-control-center
The following packages will be REMOVED:
  systemd-shim
The following packages will be upgraded:
  gnome-session-bin gnome-session-common indicator-session libpam-systemd systemd
  ubuntu-session upstart
7 upgraded, 0 newly installed, 1 to remove and 1776 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,031 kB of archives.
After this operation, 9,839 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 456544 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by westie457 on 2017-07-16
What does ```
dpkg --configure -a
```tell us?

Post the output please.

---

### Post by reut2 on 2017-07-16
```
root@reuven-Ubuntu:/home/reuven# dpkg --configure -a
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-session-bin (>= 3.20.2-1ubuntu7); however:
  Version of gnome-session-bin on system is 3.18.1.2-1ubuntu1.16.04.2.
 gnome-session depends on gnome-session-common (= 3.20.2-1ubuntu7); however:
  Version of gnome-session-common on system is 3.18.1.2-1ubuntu1.16.04.2.

dpkg: error processing package gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-session; however:
  Package gnome-session is not configured yet.

dpkg: error processing package gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent processing triggers for systemd:
 systemd depends on libsystemd0 (= 229-4ubuntu17); however:
  Version of libsystemd0:amd64 on system is 231-9ubuntu5.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving triggers unprocessed
Errors were encountered while processing:
 gnome-session
 gnome-shell
 systemd


```

---

### Post by Bashing-om on 2017-07-17
reut2; Hummm ...

Where are these elevated version comong from ?
The correct versions:
> 
sysop@x1604:~$ apt list gnome-session-bin
Listing... Done
gnome-session-bin/xenial-updates 3.18.1.2-1ubuntu1.16.04.2 amd64
N: There is 1 additional version. Please use the '-a' switch to see it
sysop@x1604:~$ apt list libsystemd0
Listing... Done
libsystemd0/xenial-updates,now 229-4ubuntu17 amd64 [installed]
N: There are 2 additional versions. Please use the '-a' switch to see them.
sysop@x1604:~$


Post back:
```

apt policy gnome-session-bin
apt policy nome-session
apt policy gnome-shell
apt policy libsystemd0

```
See what you have done that breaks the package manager .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by reut2 on 2017-07-17
I don't know if this makes a difference, but I'm using Xubuntu-Desktop

```
root@reuven-Ubuntu:/home/reuven# **apt policy gnome-session-bin**
gnome-session-bin:
  Installed: 3.18.1.2-1ubuntu1.16.04.2
  Candidate: 3.20.2-1ubuntu7
  Version table:
     3.20.2-1ubuntu7 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 Packages
 *** 3.18.1.2-1ubuntu1.16.04.2 100
        100 /var/lib/dpkg/status


root@reuven-Ubuntu:/home/reuven# **apt policy nome-session**
N: Unable to locate package nome-session


root@reuven-Ubuntu:/home/reuven# **apt policy gnome-shell**
gnome-shell:
  Installed: 3.20.4-0ubuntu3
  Candidate: 3.20.4-0ubuntu3
  Version table:
 *** 3.20.4-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     3.20.4-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages


root@reuven-Ubuntu:/home/reuven# **apt policy libsystemd0**
libsystemd0:
  Installed: 231-9ubuntu5
  Candidate: 231-9ubuntu5
  Version table:
 *** 231-9ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu yakkety-security/main amd64 Packages
        100 /var/lib/dpkg/status
     231-9git1 500


```

---

### Post by Bashing-om on 2017-07-17
reut2; Humm ....

yakkety - think'n
> 
Package gnome-session-bin
yakkety (16.10) (gnome): GNOME Session Manager - Minimal runtime 
3.20.2-1ubuntu7: amd64 arm64 armhf i386 powerpc ppc64el s390x

Package gnome-session-common
yakkety (16.10) (gnome): GNOME Session Manager - common files 
3.20.2-1ubuntu7: all

Package gnome-session
yakkety (16.10) (gnome): GNOME Session Manager - GNOME 3 session [universe] 
3.20.2-1ubuntu7: all

Package libsystemd0
yakkety-updates (libs): systemd utility library 
231-9ubuntu5: amd64 arm64 armhf i386 powerpc ppc64el s390x
Package libsystemd0
yakkety (16.10) (libs): systemd utility library 
231-9ubuntu5 [security]: amd64 i386 
231-9git1 [ports]: arm64 armhf powerpc ppc64el s390x


As my brain is miss-firing presently -- will take a bit of time.

[INDENT][INDENT]study twice ->
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-07-18
reut2; Thought .

Let's clean up (*** 3.18.1.2-1ubuntu1.16.04.2 100 >> 100 /var/lib/dpkg/status ). Then see if the package manager will explicitly install the 3.20.2-1ubuntu7 version of gnome-session-bin.
Run terminal commands :
```

sudo apt clean
sudo apt autoremove
sudo apt install gnome-session-bin=3.20.2-1ubuntu7

```

else; we get the more aggressive .

[INDENT]right or wrong
[INDENT][INDENT][INDENT]do something :)
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by reut2 on 2017-07-18
Here is the from the code you suggested: Seemingly still no change :(

```
root@reuven-Ubuntu:/home/reuven# [B]apt clean
[/B]
root@reuven-Ubuntu:/home/reuven# **apt autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gnome-session : Depends: gnome-session-bin (>= 3.20.2-1ubuntu7) but 3.18.1.2-1ubuntu1.16.04.2 is installed
                 Depends: gnome-session-common (= 3.20.2-1ubuntu7) but 3.18.1.2-1ubuntu1.16.04.2 is installed
 systemd : Depends: libsystemd0 (= 229-4ubuntu17) but 231-9ubuntu5 is installed
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:56
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
E: Unmet dependencies. Try using -f.

root@reuven-Ubuntu:/home/reuven# **apt install gnome-session-bin=3.20.2-1ubuntu7**
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-session : Depends: gnome-session-common (= 3.20.2-1ubuntu7) but 3.18.1.2-1ubuntu1.16.04.2 is to be installed
 systemd : Depends: libsystemd0 (= 229-4ubuntu17) but 231-9ubuntu5 is to be installed
 ubuntu-session : Depends: gnome-session-bin (< 3.19) but 3.20.2-1ubuntu7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2017-07-18
reut2; Hummm ........

Unforeseen turn of events . Wonder what is going on here .
Presently I do not see what could be holding up progress.
We get any hints:
```

sudo apt install gnome-session-common=3.20.2-1ubuntu7

```

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by reut2 on 2017-07-19
Still not working:
```
oot@reuven-Ubuntu:/home/reuven# apt install gnome-session-common= 3.20.2-1ubuntu7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '' for 'gnome-session-common' was not found
E: Unable to locate package 3.20.2-1ubuntu7
E: Couldn't find any package by glob '3.20.2-1ubuntu7'
E: Couldn't find any package by regex '3.20.2-1ubuntu7'


```

---

### Post by ian-weisser on 2017-07-19
> **reut2 said:**
> I upgraded a few days ago, now I'm getting messages that I have unmet dependencies:

Your upgrade partially failed.
You should have received quite a few error messages about it.


> Depends: gnome-session-bin (>= 3.20.2-1ubuntu7) but 3.18.1.2-1ubuntu1.16.04.2 is installed
3.18.1.2-1ubuntu1.16.04.2 is 16.04
3.20.2-1ubuntu7 is in 16.10 (EOL Soon!!)


You have *something* installed that depends upon the 16.04 version. We don't know what - only you can tell us that.
This sort of problem usually happens when users add PPAs or other non-Ubuntu software, then forget to uninstall it before upgrading to the next release of Ubuntu. 

> W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:56
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55

Not-coincidentally, did you notice that your sources are borked, too? Seems you did try to install something.
Search your memory until you recall what you installed, then uninstall it.
Then your package manager should work again.

Once your package manager is working, upgrade to 17.04 very soon.
Then, and only then, re-install the 17.04 version of your desired software.

---

### Post by Bashing-om on 2017-07-19
> **reut2 said:**
> Still not working:
```
oot@reuven-Ubuntu:/home/reuven# apt install gnome-session-common= 3.20.2-1ubuntu7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '' for 'gnome-session-common' was not found
E: Unable to locate package 3.20.2-1ubuntu7
E: Couldn't find any package by glob '3.20.2-1ubuntu7'
E: Couldn't find any package by regex '3.20.2-1ubuntu7'


```

Silly little space - corrected in the post ( common= 3.20.2-1ubuntu7) -- common=3.20.2-1ubuntu7

-Haste makes waste-

---

### Post by reut2 on 2017-07-20
Could this all have something to do with which repositories the system is setup to look in?

Somewhat unintentionally I updated to Zesty  And I'm getting the same issues.

here is what I have:
/etc/apt/sources.list
> # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner

deb [http://archive.canonical.com/](http://archive.canonical.com/) zesty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) zesty partner
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security main
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security main
# deb [http://ppa.launchpad.net/texworks/stable/ubuntu](http://ppa.launchpad.net/texworks/stable/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/texworks/stable/ubuntu](http://ppa.launchpad.net/texworks/stable/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner


files in /etc/apt/sources.list.d/
> dropbox.list                                     flexiondotorg-hal-flash-trusty.list.save  google-chrome.list.distUpgrade
dropbox.list.distUpgrade                         getdeb.list                               texworks-stable-trusty.list
dropbox.list.save                                 getdeb.list.distUpgrade                    texworks-stable-trusty.list.distUpgrade
flexiondotorg-hal-flash-trusty.list              getdeb.list.save                          texworks-stable-trusty.list.save
flexiondotorg-hal-flash-trusty.list.distUpgrade  google-chrome.list



```
root@reuven-Ubuntu:/# **apt-get update**
Hit:1 http://us.archive.ubuntu.com/ubuntu zesty InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                           
Get:3 http://us.archive.ubuntu.com/ubuntu zesty-updates InRelease [89.2 kB]            
Get:4 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]                                      
Hit:5 http://archive.canonical.com/ubuntu zesty InRelease                                                            
Get:6 http://us.archive.ubuntu.com/ubuntu zesty-backports InRelease [89.2 kB]
Get:7 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]                                   
Get:8 http://us.archive.ubuntu.com/ubuntu zesty-security InRelease [89.2 kB]                                          
Hit:9 http://archive.canonical.com zesty InRelease                                 
Get:10 http://us.archive.ubuntu.com/ubuntu zesty-updates/main Sources [64.6 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu zesty-updates/universe Sources [23.7 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu zesty-updates/main amd64 Packages [159 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu zesty-updates/main i386 Packages [157 kB] 
Get:14 http://us.archive.ubuntu.com/ubuntu zesty-updates/main Translation-en [72.1 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu zesty-updates/main amd64 DEP-11 Metadata [47.3 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu zesty-updates/main DEP-11 64x64 Icons [18.0 kB]    
Get:17 http://us.archive.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages [84.1 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu zesty-updates/universe i386 Packages [84.0 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu zesty-updates/universe Translation-en [49.1 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu zesty-updates/universe amd64 DEP-11 Metadata [71.4 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu zesty-updates/universe DEP-11 64x64 Icons [80.8 kB]       
Get:22 http://us.archive.ubuntu.com/ubuntu zesty-updates/multiverse amd64 DEP-11 Metadata [5,836 B]
Get:23 http://us.archive.ubuntu.com/ubuntu zesty-backports/universe amd64 DEP-11 Metadata [4,684 B]
Get:24 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,394 B]
Get:25 http://us.archive.ubuntu.com/ubuntu zesty-security/main Sources [35.7 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu zesty-security/main amd64 Packages [104 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu zesty-security/main i386 Packages [103 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu zesty-security/main amd64 DEP-11 Metadata [11.7 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu zesty-security/universe amd64 Packages [51.3 kB]    
Get:30 http://us.archive.ubuntu.com/ubuntu zesty-security/universe i386 Packages [51.3 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu zesty-security/universe amd64 DEP-11 Metadata [14.4 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu zesty-security/universe DEP-11 64x64 Icons [31.0 kB]
Fetched 1,595 kB in 1s (851 kB/s)                                                        

(appstreamcli:4268): GLib-[COLOR=#ff00cc]CRITICAL[/COLOR] **: g_strchug: assertion 'string != NULL' failed

(appstreamcli:4268): GLib-[COLOR=#ff00cc]CRITICAL[/COLOR] **: g_strchomp: assertion 'string != NULL' failed

(appstreamcli:4268): GLib-[COLOR=#ff00cc]CRITICAL[/COLOR] **: g_strchug: assertion 'string != NULL' failed

(appstreamcli:4268): GLib-[COLOR=#ff00cc]CRITICAL[/COLOR] **: g_strchomp: assertion 'string != NULL' failed
Reading package lists... Done
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:56
W:  Target Packages (main/binary-amd64/Packages) is configured multiple  times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W:  Target Packages (main/binary-i386/Packages) is configured multiple times  in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  Packages (main/binary-all/Packages) is configured multiple times in  /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  Translations (main/i18n/Translation-en_US) is configured multiple times  in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  Translations (main/i18n/Translation-en) is configured multiple times in  /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in  /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times  in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:56
W:  Target Packages (main/binary-amd64/Packages) is configured multiple  times in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W:  Target Packages (main/binary-i386/Packages) is configured multiple times  in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  Packages (main/binary-all/Packages) is configured multiple times in  /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  Translations (main/i18n/Translation-en_US) is configured multiple times  in /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  Translations (main/i18n/Translation-en) is configured multiple times in  /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in  /etc/apt/sources.list:39 and /etc/apt/sources.list:55
W: Target  DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times  in /etc/apt/sources.list:39 and /etc/apt/sources.list:55

```

---

### Post by Bashing-om on 2017-07-21
reut2; Uh Huh;
Short answer to:
> 
Could this all have something to do with which repositories the system is setup to look in?

Yes.

Show us - easier to identify the lines:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

And we start to get somewhere .

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by reut2 on 2017-09-07
So I finally did a clean install of Xubuntu 16.04, and all is well.

Thank you for all your help!

---

### Post by Bashing-om on 2017-09-07
reut2; :)

> **reut2 said:**
> So I finally did a clean install of Xubuntu 16.04, and all is well.

Thank you for all your help!

Help is what we do . - That nuclear solution always works !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

