---
title: "is it still possible to upgrade from 10.04 to 12.04?"
date: 2015-02-04
forum: Installation &amp; Upgrades
---

### Post by acidrop on 2015-02-04
hello

I have an old box with ubuntu 10.04 lts installed.
I would like to upgrade to 12.04 lts if possible.

Below follows some info:

>  lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

> uname -a
Linux ubuntu-server 2.6.32-65-generic #131-Ubuntu SMP Fri Aug 15 20:39:31 UTC 2014 x86_64 GNU/Linux

> cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## Unsupported open source software
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe

## Unsupported software of questonable license status (not open source)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Security updates repository
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse


> cat /etc/update-manager/release-upgrades
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

I did "sudo apt-get update" , "sudo apt-get upgrade" , "sudo apt-get dist-upgrade" and installed all updates.

Then...

>  sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

>  sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found

What am I missing? Isn't this kind of upgrade supported anymore?

thank you

---

### Post by Bucky Ball on 2015-02-04
Try [this]("https://help.ubuntu.com/community/EOLUpgrades").

As 10.04 has reached end-of-life, the option to upgrade to 12.04 LTS might not appear as an option when you go for a regular update (I think that's where it used to appear).

---

### Post by slickymaster on 2015-02-04
Or [this]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS").

---

### Post by Bucky Ball on 2015-02-04
> **slickymaster said:**
> Or [this]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS").

Better than my link. As I say, though, not sure if the option to upgrade will show as 10.04 LTS is EOL. You can certainly try your luck and let us know. I'm curious. ;)

---

### Post by slickymaster on 2015-02-04
> **Bucky Ball said:**
> Better than my link. As I say, though, not sure if the option to upgrade will show as 10.04 LTS is EOL. You can certainly try your luck, though, and let us know. I'm curious. ;)
Good point, Bucky. Now you left me curios, also. :p

---

### Post by acidrop on 2015-02-04
thank you both for the suggestions!
Actually I have came accross this Wikis before and tried to follow the written procedure but with no luck.
As I mentioned on my first post I have already followed most of the official guidelines unsuccessfully though..
Can you please point me to something specific that I have missed? (I have already done "sudo aptitude install update-manager-core update-manager")

---

### Post by slickymaster on 2015-02-04
Have you already checked: [How to install software or upgrade from an old unsupported release?]("http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release")

---

### Post by acidrop on 2015-02-04
I've changed repos to "old-releases.ubuntu.com" and did "sudo apt-get update && sudo apt-get dist-upgrade" , sudo do-release-upgrade" without luck...

---

### Post by acidrop on 2015-02-04
I will try "Upgrading Using the Alternate CD/DVD" as described [here]("https://help.ubuntu.com/community/PreciseUpgrades") and see what happens...

---

### Post by acidrop on 2015-02-04
Although installation from cdrom started promising it failed after downloading the packages for precise with the following error:

> ....Failed to fetch cdrom:[Ubuntu-Server 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140806.1)]/pool/main/v/vbetool/vbetool_1.1-2ubuntu1_amd64.deb Hash
Sum mismatch
Failed to fetch cdrom:[Ubuntu-Server 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140806.1)]/pool/main/w/w3m/w3m_0.5.3-5ubuntu1.1_amd64.deb Hash Sum
mismatch
Failed to fetch cdrom:[Ubuntu-Server 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140806.1)]/pool/main/libn/libnet-daemon-perl/libnet-daemon-perl_0.48-1_all.deb
Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu-Server 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140806.1)]/pool/main/l/lsb/lsb-core_4.0-0ubuntu20.3_amd64.deb Hash
Sum mismatch
Failed to fetch cdrom:[Ubuntu-Server 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140806.1)]/pool/main/l/lsb/lsb-cxx_4.0-0ubuntu20.3_amd64.deb Hash
Sum mismatch
Failed to fetch cdrom:[Ubuntu-Server 12.04.5 LTS _Precise Pangolin_ -
Release amd64
(20140806.1)]/pool/main/s/ssh-import-id/ssh-import-id_2.10-0ubuntu1_all.deb
Hash Sum mismatch



Restoring original system state

Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done


---

### Post by mörgæs on 2015-02-04
10.04 to 14.04 is a long step and much can go wrong.

I recommend that you wait a day or two for 14.04.2 to be released and do a clean install.

---

### Post by Bucky Ball on 2015-02-04
> **mörgæs said:**
> 10.04 to 14.04 is a long step and much can go wrong.



OP is wanting to go from 10.04 to 12.04 LTS, but your comment still applies. 10.04 was Gnome, 12.04 is Unity. That can be problematic in itself.

---

