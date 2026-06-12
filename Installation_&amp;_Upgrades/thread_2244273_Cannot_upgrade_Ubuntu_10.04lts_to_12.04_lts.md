---
title: "Cannot upgrade Ubuntu 10.04lts to 12.04 lts"
date: 2014-09-15
forum: Installation &amp; Upgrades
---

### Post by acidrop on 2014-09-15
Hello

I have a box with Ubuntu 10.04 lts which I am trying to upgrade to 12.04 lts unsuccessfully.

```
Linux ubuntu 2.6.32-65-generic #131-Ubuntu SMP Fri Aug 15 20:39:31 UTC 2014 x86_64 GNU/Linux
```

```
 lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

```

```
cat /etc/apt/sources.list
deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid main restricted
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted

## Unsupported open source software
deb http://old-releases.ubuntu.com/ubuntu/ lucid universe
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid universe
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid-updates universe

## Unsupported software of questonable license status (not open source)
deb http://old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse

## Security updates repository
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

```
cat /etc/update-manager/
meta-release        release-upgrades    release-upgrades.d/
acid@ubuntu-server:~$ cat /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
prompt=lts
```

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
```

Any suggestion?

thank you

---

### Post by Bucky Ball on 2014-09-15
Are you invited to upgrade along the top of the Update Manager window when you open Update Manager?

I am presuming you did:

```
sudo apt-get update
```

... prior to:

```
sudo apt-get upgrade
```

After that, did you also do:

```
sudo apt-get dist-upgrade
```

I don't imagine there'd be much available to upgrade, though. Could be that 10.04 LTS has been EOL for a while now and is not being given the option to go that route. There may be a way around that, might need be a clean install, but there is some clue of where to search next. :-k

Incidentally, if you do get things working, good idea to switch off any third-party PPAs that you have manually installed. They can cause major/minor headaches during an upgrade the way you're planning.

---

### Post by acidrop on 2014-09-15
No, I am not invited neither from Update Manager.

---

### Post by Bucky Ball on 2014-09-15
How about this:

> Note that if you&#8217;re upgrading from 10.04 LTS, do-release-upgrade will complain &#8220;No new release found&#8221; until 12.04.1 is released. To force an upgrade, use the -d option. See Ask Ubuntu for more information. 

From [HERE.]("https://help.ubuntu.com/community/PreciseUpgrades#Upgrade_from_11.10_to_12.04_LTS_and_10.04_LTS_to_12.04_LTS") Force it with -d and see if that works. 12.04 is up to .5, but probably won't work if the option to upgrade is unavaible in 10.04 for other reasons.

---

### Post by acidrop on 2014-09-15
No even that didn't help.

---

### Post by Bucky Ball on 2014-09-15
Same response? Nothing available?

---

### Post by acidrop on 2014-09-15
thank you for your assistance!

Yes, I did sudo apt-get update and upgrade and the do-release-upgrade -d

```
sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found
```

I do not have any third party ppa enabled at the moment.

Now I am trying by using alternate cd method by running cdromupgrade script... let's see what happens..

---

### Post by Bucky Ball on 2014-09-15
On [that same link]("https://help.ubuntu.com/community/PreciseUpgrades#Upgrade_from_11.10_to_12.04_LTS_and_10.04_LTS_to_12.04_LTS"), go down the page a bit and try the other upgrading options, particularly the 'Upgrade with Alternate CD' one.

* Update: Scratch that. I see you're already doing it. Any luck? There is also a torrent method there.

---

### Post by acidrop on 2014-09-15
Tried alternate cd method. It started the upgrade process but after a while fails with the following:


```
Failed to fetch cdrom:[Ubuntu 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140807)]/pool/main/u/ubuntuone-control-panel/ubuntuone-control-panel_3.0.1-0ubuntu1_all.deb
Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140807)]/pool/main/u/ubuntuone-couch/ubuntuone-couch_0.3.0-0ubuntu4_all.deb
Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140807)]/pool/main/u/ubuntuone-installer/ubuntuone-installer_3.0.2-0ubuntu1.1_all.deb
Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140807)]/pool/main/x/xfonts-mathml/xfonts-mathml_4ubuntu1_all.deb
Hash Sum mismatch



Restoring original system state

Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
=== Command detached from window (Mon Sep 15 12:47:52 2014) ===
=== Command terminated with exit status 1 (Mon Sep 15 12:47:52 2014) ===
```

---

### Post by Bucky Ball on 2014-09-15
This repeated error:

> Hash Sum mismatch

... has me thinking the ISO may be defective. Did you torrent it or regular download? Check the md5sum before burning the CD? I would do that.

---

### Post by Bucky Ball on 2014-09-15
Hey, acidrop, you might like to read on from here:

[http://ubuntuforums.org/showthread.php?t=2221550&p=13011705&viewfull=1#post13011705](http://ubuntuforums.org/showthread.php?t=2221550&p=13011705&viewfull=1#post13011705)

Might get some clues. Try the EOL repository Elfy mentions in post #5.

---

### Post by acidrop on 2014-09-15
I verified md5sum and re-downloaded the file from different source but again I get "Hash Sum mismatch".

---

### Post by Bucky Ball on 2014-09-15
Have you tried the link in my last post? (#11) ;)

---

