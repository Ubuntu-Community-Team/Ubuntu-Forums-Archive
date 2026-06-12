---
title: "Upgrade Errors in both system and firefox"
date: 2018-07-14
forum: Installation &amp; Upgrades
---

### Post by kennbmondo on 2018-07-14
I am using Ubuntu 16.04

```
sudo apt-get install --reinstall firefox
[sudo] password for kennbrown: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 chromium-browser : Depends: chromium-codecs-ffmpeg-extra (= 66.0.3359.181-0ubuntu0.16.04.1) but 63.0.3239.84-0ubuntu0.16.04.1 is to be installed or
                             chromium-codecs-ffmpeg (= 66.0.3359.181-0ubuntu0.16.04.1) but it is not going to be installed
 chromium-browser-l10n : Depends: chromium-browser (< 63.0.3239.132-0ubuntu0.16.04.1.1~) but 66.0.3359.181-0ubuntu0.16.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by deadflowr on 2018-07-14
Run
```
sudo apt update
sudo apt full-upgrade
```
post back results.

---

### Post by kennbmondo on 2018-07-14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 chromium-browser-l10n : Depends: chromium-browser (>= 63.0.3239.132-0ubuntu0.16.04.1) but 63.0.3239.84-0ubuntu0.16.04.1 is installed
E: Unmet dependencies. Try using -f.

help!

apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

In 2 years I have never had any of these problems and I am dubious about upgrading to newer versions.

---

### Post by deadflowr on 2018-07-14
I asked for the output of the commands I posted.
The full output, please.

Edit:
The commands posted will only update the current system, and not upgrade releases.
(That command is something else entirely)

---

### Post by kennbmondo on 2018-07-14
Damn. I just checked and it has already upgraded me to 16.04... now what?

```
kennbrown@kennbrown-HP-Compaq-6730b-FS739LA-ABM:~$ sudo apt update
[sudo] password for kennbrown: 
Sorry, try again.
[sudo] password for kennbrown: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
382 packages can be upgraded. Run 'apt list --upgradable' to see them.
kennbrown@kennbrown-HP-Compaq-6730b-FS739LA-ABM:~$
```

```
kennbrown@kennbrown-HP-Compaq-6730b-FS739LA-ABM:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 chromium-browser-l10n : Depends: chromium-browser (>= 63.0.3239.132-0ubuntu0.16.04.1) but 63.0.3239.84-0ubuntu0.16.04.1 is installed
E: Unmet dependencies. Try using -f.
kennbrown@kennbrown-HP-Compaq-6730b-FS739LA-ABM:~$
```

apt-get-f install does not work either

---

### Post by deadflowr on 2018-07-14
Hm, 
what do
```
apt policy chromium-browser
apt policy chromium-browser-l10n
```
show?

---

### Post by kennbmondo on 2018-07-14
Thanx for your time but I guess my limited experience hampers my ability to problem solve. Cheers.

```
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 chromium-browser-l10n all 66.0.3359.181-0ubuntu0.16.04.1 [2 724 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 chromium-browser amd64 66.0.3359.181-0ubuntu0.16.04.1 [52.2 MB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 chromium-codecs-ffmpeg-extra amd64 66.0.3359.181-0ubuntu0.16.04.1 [1 018 kB]
Fetched 55.9 MB in 14s (3 891 kB/s)                                            
(Reading database ... 431530 files and directories currently installed.)
Preparing to unpack .../chromium-browser-l10n_66.0.3359.181-0ubuntu0.16.04.1_all.deb ...
Unpacking chromium-browser-l10n (66.0.3359.181-0ubuntu0.16.04.1) over (63.0.3239.132-0ubuntu0.16.04.1) ...
Preparing to unpack .../chromium-browser_66.0.3359.181-0ubuntu0.16.04.1_amd64.deb ...
Unpacking chromium-browser (66.0.3359.181-0ubuntu0.16.04.1) over (63.0.3239.84-0ubuntu0.16.04.1) ...
Preparing to unpack .../chromium-codecs-ffmpeg-extra_66.0.3359.181-0ubuntu0.16.04.1_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (66.0.3359.181-0ubuntu0.16.04.1) over (63.0.3239.84-0ubuntu0.16.04.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up chromium-codecs-ffmpeg-extra (66.0.3359.181-0ubuntu0.16.04.1) ...
Setting up chromium-browser (66.0.3359.181-0ubuntu0.16.04.1) ...
Setting up chromium-browser-l10n (66.0.3359.181-0ubuntu0.16.04.1) ...
kennbrown@kennbrown-HP-Compaq-6730b-FS739LA-ABM:~$
```

I actually want Chromium gone for the current time... it seems to cause no end of problems for me.

I cannot even access the {remove{ function in the sys files....

---

### Post by deadflowr on 2018-07-14
To remove chromium run
```
sudo apt purge chromium-browser
```

(Note that you'll need to do the full-upgrade command eventually, so the system will be fully up-to-date.)
> I cannot even access the {remove{ function in the sys files.... 
What?

> I just checked and it has already upgraded me to 16.04... now what?
It was assumed you were on 16.04 from the very first line of post #1.

---

