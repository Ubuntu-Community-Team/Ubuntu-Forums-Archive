---
title: "disgruntled newbie...please help!"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by thegutterpoet on 2011-11-05
i installed ubuntu 11.10 today, seemed to go fine and dandy. i ran the update package after installing, also downloaded a couple of packages which i did not install. tried for skype, but it wouldnt work...and then...all of a sudden, i cannot install anything, every entrance into the software centre brings up and error:-

[I]Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details-
[/I][I]flashplugin-installer: Depends: flashplugin-downloader (>= 11.0.1.152ubuntu1) but it is not installed
nspluginwrapper: Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is installed
                 Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.21.6-3ubuntu3 is installed
                 Depends: libglib2.0-0 (>= 2.16.0) but 2.30.0-0ubuntu4 is installed
                 Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.6-0ubuntu5 is installed
                 Depends: nspluginviewer (= 1.4.4-0ubuntu3) but it is not installed
skype: Depends: ia32-libs (>= 2008080:cool: but it is not installed
       Depends: lib32asound2 (> 1.0.24.1) but it is not installed
       Depends: lib32gcc1 (>= 1:4.1.1) but it is not installed
       Depends: lib32stdc++6 (>= 4.2.1) but it is not installed
       Depends: libc6-i386 (>= 2.4) but it is not installed[/I]


I try to run the apt-get install -f command, but then get told:
[I]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/I]

any help is appreciated...

the start of the problem is when i head to the software centre or try to install something elsewhere-
[I]'items cannot be installed or removed until the package catalogue is repaired. do you want to repair it now?

once update manager has finished the repairs, you can close it and return to the store.'[/I]

so i head to repair...leads to -

'There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.'

the details seem to change..

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by IWantFroyo on 2011-11-05
```
sudo apt-get install -f
```

If you don't put 'sudo', it won't work.

---

### Post by Rubi1200 on 2011-11-05
You can also try this after IWantFroyo's suggestion:

```
sudo dpkg --configure -a
```

Post back with error messages.

---

### Post by thegutterpoet on 2011-11-05
> **IWantFroyo said:**
> ```
sudo apt-get install -f
```If you don't put 'sudo', it won't work.
 this command led to this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ia32-libs lib32asound2 lib32bz2-1.0 lib32ffi6 lib32gcc1 lib32ncurses5
  lib32ncursesw5 lib32stdc++6 lib32tinfo5 lib32z1 libc6-i386
  ttf-mscorefonts-installer
Suggested packages:
  lib32asound2-plugins
Recommended packages:
  ia32-libs-multiarch
The following packages will be REMOVED:
  flashplugin-installer nspluginwrapper
The following NEW packages will be installed:
  ia32-libs lib32asound2 lib32bz2-1.0 lib32ffi6 lib32gcc1 lib32ncurses5
  lib32ncursesw5 lib32stdc++6 lib32tinfo5 lib32z1 libc6-i386
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 11 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 35.3 MB of archives.
After this operation, 132 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/multiverse ttf-mscorefonts-installer all 3.3ubuntu4 [34.8 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main libc6-i386 amd64 2.13-20ubuntu5 [3,851 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32gcc1 amd64 1:4.6.1-9ubuntu3 [54.1 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32z1 amd64 1:1.2.3.4.dfsg-3ubuntu3 [49.4 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32stdc++6 amd64 4.6.1-9ubuntu3 [340 kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32asound2 amd64 1.0.24.1-0ubuntu10 [392 kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32bz2-1.0 amd64 1.0.5-6ubuntu1 [32.7 kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32tinfo5 amd64 5.9-1ubuntu5 [63.2 kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32ncurses5 amd64 5.9-1ubuntu5 [139 kB]
Get:10 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32ffi6 amd64 3.0.11~rc1-2 [16.4 kB]
Get:11 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/main lib32ncursesw5 amd64 5.9-1ubuntu5 [169 kB]
Get:12 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) oneiric/universe ia32-libs amd64 20090808ubuntu26 [30.1 MB]
Fetched 35.3 MB in 3min 10s (186 kB/s)                                         
Preconfiguring packages ...
dpkg: error: configuration error: /etc/dpkg/dpkg.cfg.d/multiarch:1: unknown option 'Reading'
E: Sub-process /usr/bin/dpkg returned an error code (2)


> **Rubi1200 said:**
> You can also try this after IWantFroyo's suggestion:

```
sudo dpkg --configure -a
```Post back with error messages.
this command led to this:

dpkg: error: configuration error: /etc/dpkg/dpkg.cfg.d/multiarch:1: unknown option 'Reading'

any more ideas please!

---

### Post by bluexrider on 2011-11-05
File manager as root
go to >  /etc/dpkg/dpkg.cfg.d
Remove /multiarch:1: file

Run in terminal sudo apt-get update
then sudo apt-get dist-upgrade

---

### Post by thegutterpoet on 2011-11-05
> **bluexrider said:**
> File manager as root
go to >  /etc/dpkg/dpkg.cfg.d
Remove /multiarch:1: file

Run in terminal sudo apt-get update
then sudo apt-get dist-upgrade

sudo apt-get update

ran fine

sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 flashplugin-installer : Depends: flashplugin-downloader (>= 11.0.1.152ubuntu1) but it is not installable
 nspluginwrapper : Depends: nspluginviewer (= 1.4.4-0ubuntu3) but it is not installable
 skype : Depends: ia32-libs (>= 20080808) but it is not installed
         Depends: lib32asound2 (> 1.0.24.1) but it is not installed
         Depends: lib32gcc1 (>= 1:4.1.1) but it is not installed
         Depends: lib32stdc++6 (>= 4.2.1) but it is not installed
         Depends: libc6-i386 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.

so I try apt-get -f install

which pops up a purple screen - configuring ttf-mscorefonts-installer
I used tab and return...it ran through the process in the terminal...

all done..

and my software centre error has vanished...cheers!

---

### Post by Rubi1200 on 2011-11-06
Excellent! Glad you got this sorted out in the end :)

Please mark this Solved using the Thread Tools near the top of the page.

---

