---
title: "Update Manager / Synaptic Package Manager return errors"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by david wise on 2011-12-14
When I open Synaptic, the message
> You have 3 broken packages on your system!

Use the "Broken" filter to locate them.

The Broken filter just displays all required updates.



When I open Update Manager 34 updates are listed as selected / downloaded, but not installed.  When I attempt to install the following dialog appears:
> Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Details:
> The following packages have unmet dependencies:

libsyncdaemon-1.0-1: Depends: libc6 (>= 2.3.6-6~) but 2.13-0ubuntu13 is installed
                     Depends: libglib2.0-0 (>= 2.24.0) but 2.28.6-0ubuntu1 is installed
                     Depends: ubuntuone-client (>= 1.6.2-0ubuntu2) but 1.6.2-0ubuntu1 is installed
ubuntuone-client: Depends: gconf2 (>= 2.28.1-2) but 2.32.2-0ubuntu2 is installed
                  Depends: python-ubuntuone-client (= 1.6.2-0ubuntu1) but 1.6.2-0ubuntu2 is installed
                  Depends: gir1.2-unity-3.0 (>= 3.8.4) but 3.8.4-0ubuntu1 is installed
ubuntuone-client-gnome: Depends: libatk1.0-0 (>= 1.12.4) but 2.0.0-0ubuntu1 is installedthird party repositories
                        Depends: libc6 (>= 2.3.6-6~) but 2.13-0ubuntu13 is installed
                        Depends: libcamel1.2-19 (>= 2.32) but 2.32.2-0ubuntu2 is installed
                        Depends: libebook1.2-10 (>= 2.32.2) but 2.32.2-0ubuntu2 is installed
                        Depends: libedataserver1.2-14 (>= 2.32.2) but 2.32.2-0ubuntu2 is installed
                        Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-2.1ubuntu3 is installed
                        Depends: libfreetype6 (>= 2.2.1) but 2.4.4-1ubuntu2.2 is installed
                        Depends: libgconf2-4 (>= 2.31.1) but 2.32.2-0ubuntu2 is installed
                        Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.23.3-0ubuntu1 is installed
                        Depends: libglib2.0-0 (>= 2.18.0) but 2.28.6-0ubuntu1 is installed
                        Depends: libgtk2.0-0 (>= 2.20.0) but 2.24.4-0ubuntu2 is installed
                        Depends: libnautilus-extension1 (>= 2.30) but 1:2.32.2.1-0ubuntu13 is installed
                        Depends: libnspr4 (>= 4.7.0~1.9b1) but 4.8.7-0ubuntu1 is installed
                        Depends: libnss3 (>= 3.12.2~rc1) but 3.12.9+ckbi-1.82-0ubuntu2.1 is installed
                        Depends: libpango1.0-0 (>= 1.14.0) but 1.28.4-0ubuntu1 is installed
                        Depends: libsoup2.4-1 (>= 2.4.0) but 2.34.0-0ubuntu1.1 is installed
                        Depends: libsqlite3-0 (>= 3.7.3) but 3.7.4-2ubuntu5 is installed
                        Depends: libxml2 (>= 2.6.27) but 2.7.8.dfsg-2ubuntu0.1 is installed
                        Depends: ubuntuone-client (= 1.6.2-0ubuntu2) but 1.6.2-0ubuntu1 is installed
                        Depends: python-gtk2 (>= 2.10) but 2.22.0-0ubuntu1.1 is installed


I disabled third party repositories, and reran with the same result.

Can anyone provide a little direction in this matter?

---

### Post by BC59 on 2011-12-14
First of all run in a terminal:

```
sudo dpkg --configure -a
``` and then

```
sudo apt-get install -f
```

---

### Post by david wise on 2011-12-14
Those commands still yield errors:

sudo dpkg --configure -a
> david2@david2-Dimension-4700:~$ sudo dpkg --configure -a
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 10053 package 'compiz-plugins':
 'Replaces' field, reference to 'compiz-fusion-plugins-extra': error in version: invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23359 package 'totem-plugins':
 missing description
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.6.2-0ubuntu2); however:
  Version of ubuntuone-client on system is 1.6.2-0ubuntu1.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.6.2-0ubuntu2); however:
  Version of ubuntuone-client on system is 1.6.2-0ubuntu1.
dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntuone-client-gnome
 libsyncdaemon-1.0-1


sudo apt-get install -f
> david2@david2-Dimension-4700:~$ sudo apt-get install -f
Reading package lists... Error!
E: Malformed 2nd word in the Status line
E: Error occurred while processing x11-apps (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


---

### Post by david wise on 2011-12-14
Those commands still yield errors:

sudo dpkg --configure -a
> david2@david2-Dimension-4700:~$ sudo dpkg --configure -a
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 10053 package 'compiz-plugins':
 'Replaces' field, reference to 'compiz-fusion-plugins-extra': error in version: invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23359 package 'totem-plugins':
 missing description
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.6.2-0ubuntu2); however:
  Version of ubuntuone-client on system is 1.6.2-0ubuntu1.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.6.2-0ubuntu2); however:
  Version of ubuntuone-client on system is 1.6.2-0ubuntu1.
dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntuone-client-gnome
 libsyncdaemon-1.0-1


sudo apt-get install -f
> david2@david2-Dimension-4700:~$ sudo apt-get install -f
Reading package lists... Error!
E: Malformed 2nd word in the Status line
E: Error occurred while processing x11-apps (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


---

### Post by BC59 on 2011-12-14
Run this

```
sudo dpkg --clear-avail
```

then

```
sudo apt-get update
```

---

### Post by david wise on 2011-12-14
Same thing for that one:
> david2@david2-Dimension-4700:~$ sudo dpkg --clear-avail
david2@david2-Dimension-4700:~$ sudo apt-get install -f
Reading package lists... Error!
E: Malformed 2nd word in the Status line
E: Error occurred while processing x11-apps (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


---

### Post by BC59 on 2011-12-14
Then try to change the file manually, run:

```
gksudo nautilus
```

Then from root nautilus go to File system--var--lib--dpk-->and rename the file status to status1. Then rename the status.old to status. Close nautilus and run again:

```
sudo apt-get update
```

---

### Post by david wise on 2011-12-15
More errors:

> david2@david2-Dimension-4700:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages          
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [7,755 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Fetched 1 B in 3s (0 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by BC59 on 2011-12-15
Try this

```
sudo remove /var/lib/apt/lists/partial/*
```

---

### Post by david wise on 2011-12-15
That one yields:

> david2@david2-Dimension-4700:~$ sudo remove /var/lib/apt/lists/partial/*
[sudo] password for david2: 
sudo: remove: command not found


---

### Post by BC59 on 2011-12-16
Try this:

```
sudo rm -rf /var/lib/apt/lists/partial/*
```

---

### Post by david wise on 2011-12-16
So today when I open Software Center a prompt appears requesting permission to repair the file system.  That repair ends in the following error:

> Package operation failed

installArchives() failed: dpkg: warning: parsing file '/var/lib/dpkg/status' near line 10053 package 'compiz-plugins':
 'Replaces' field, reference to 'compiz-fusion-plugins-extra': error in version: invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23359 package 'totem-plugins':
 missing description
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 157872 files and directories currently installed.)
Preparing to replace ubuntuone-client 1.6.2-0ubuntu1 (using .../ubuntuone-client_1.6.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/ubuntuone-client_1.6.2-0ubuntu2_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script was killed by signal (Segmentation fault)
Processing triggers for gconf2 ...
Segmentation fault
dpkg: error processing gconf2 (--unpack):
 subprocess installed post-installation script returned error exit status 139
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntuone-client_1.6.2-0ubuntu2_all.deb
 man-db
 gconf2
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 10054 package 'compiz-plugins':
 'Replaces' field, reference to 'compiz-fusion-plugins-extra': error in version: invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23360 package 'totem-plugins':
 missing description
Setting up man-db (2.5.9-4) ...
Updating database of manual pages ...
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.6.2-0ubuntu2); however:
  Version of ubuntuone-client on system is 1.6.2-0ubuntu1.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (2.32.2-0ubuntu2) ...
WARNING: Invalid node <dong> in a <locale> node
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.6.2-0ubuntu2); however:
  Version of ubuntuone-client on system is 1.6.2-0ubuntu1.



Any new thoughts?

---

### Post by david wise on 2011-12-16
That asks for a password, then immediately brings up another terminal prompt

---

### Post by BC59 on 2011-12-17
Try this:

```
sudo rm -rf /var/cache/apt/archives/*
```

---

