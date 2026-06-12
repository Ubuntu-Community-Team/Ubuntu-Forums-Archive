---
title: "The following packages have unmet dependencies:"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by go_beep_yourself on 2009-12-16
I can't figure out how to solve this issue. I tried disabling PPA
repos by commenting them out.

```
chris@ubuntu:~/Desktop/imageshack-uploader$ cat /etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

# winehq repository

#deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main
#deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main

# chromium daily

#deb [http://ppa.launchpad.net/timothy-redaelli/ppa/ubuntu](http://ppa.launchpad.net/timothy-redaelli/ppa/ubuntu) jaunty main
#deb-src [http://ppa.launchpad.net/timothy-redaelli/ppa/ubuntu](http://ppa.launchpad.net/timothy-redaelli/ppa/ubuntu) jaunty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main universe
restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main universe
restricted multiverse #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe main
multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main
multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports universe
main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports universe
main multiverse restricted

#miro

# deb [repo.offensive-security.com/dist/bt4]("http://repo.offensive-security.com/dist/bt4") binary/
chris@ubuntu:~/Desktop/imageshack-uploader$ sudo apt-get update
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty Release.gpg
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty/main Translation-en_US
Hit [http://archive.canonical.com]("http://archive.canonical.com/") jaunty Release.gpg
Ign [http://archive.canonical.com]("http://archive.canonical.com/") jaunty/partner Translation-en_US
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release.gpg
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-security Release.gpg
Hit [http://archive.canonical.com]("http://archive.canonical.com/") jaunty Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports Release.gpg
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/multiverse Translation-en_US
Hit [http://archive.canonical.com]("http://archive.canonical.com/") jaunty/partner Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Packages
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-security Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports Release
Hit [http://archive.canonical.com]("http://archive.canonical.com/") jaunty/partner Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Sources
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-security/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-security/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-security/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/restricted Sources
Reading package lists... Done
chris@ubuntu:~/Desktop/imageshack-uploader$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
chris@ubuntu:~/Desktop/imageshack-uploader$ sudo apt-get install
libqt4-gui libqt4-core libqt4-xml
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-core is already the newest version.
libqt4-core set to manually installed.
libqt4-xml is already the newest version.
libqt4-xml set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-gui: Depends: libqtgui4 (= 4.5.0-0ubuntu4.3) but
4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-svg (= 4.5.0-0ubuntu4.3) but
4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-opengl (= 4.5.0-0ubuntu4.3) but
4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-designer (= 4.5.0-0ubuntu4.3) but
4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-assistant (= 4.5.0-0ubuntu4.3) but
4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
E: Broken packages
chris@ubuntu:~/Desktop/imageshack-uploader$
```

---

### Post by slakkie on 2009-12-16
Yes, so your problem is what exactly? :)

Please post the full output of the error you are getting, now we have very little to go on.

---

### Post by go_beep_yourself on 2009-12-16
> **slakkie said:**
> Yes, so your problem is what exactly? :)

Please post the full output of the error you are getting, now we have very little to go on.

Did you scroll down to the bottom? Where can I get more error output?

---

### Post by slakkie on 2009-12-16
Missed the scrollbar, sorry.

could you post the output of apt-cache policy <packages>

---

### Post by go_beep_yourself on 2009-12-16
```
chris@ubuntu:~/Desktop$ apt-cache policy libqtgui4
libqtgui4:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
chris@ubuntu:~/Desktop$ apt-cache policy libqt4-gui libqt4-core libqt4-xml
libqt4-gui:
  Installed: (none)
  Candidate: 4.5.0-0ubuntu4.3
  Version table:
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-core:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-xml:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
chris@ubuntu:~/Desktop$ apt-cache policy libqt4-gui libqt4-core libqt4-xml libqtgui4 libqt4-svg libqt4-opengl libqt4-designer libqt4-assistant
libqt4-gui:
  Installed: (none)
  Candidate: 4.5.0-0ubuntu4.3
  Version table:
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-core:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-xml:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqtgui4:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-svg:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-opengl:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-designer:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
libqt4-assistant:
  Installed: 4.5.2-0ubuntu2~jaunty1~ppa2
  Candidate: 4.5.2-0ubuntu2~jaunty1~ppa2
  Version table:
 *** 4.5.2-0ubuntu2~jaunty1~ppa2 0
        100 /var/lib/dpkg/status
     4.5.0-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     4.5.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
chris@ubuntu:~/Desktop$ sudo apt-get --reinstall install  libqt4-gui libqt4-core libqt4-xml libqtgui4 libqt4-svg libqt4-opengl libqt4-designer libqt4-assistant
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libqt4-core is not possible, it cannot be downloaded.
Reinstallation of libqt4-xml is not possible, it cannot be downloaded.
Reinstallation of libqtgui4 is not possible, it cannot be downloaded.
Reinstallation of libqt4-svg is not possible, it cannot be downloaded.
Reinstallation of libqt4-opengl is not possible, it cannot be downloaded.
Reinstallation of libqt4-designer is not possible, it cannot be downloaded.
Reinstallation of libqt4-assistant is not possible, it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-gui: Depends: libqtgui4 (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-svg (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-opengl (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-designer (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-assistant (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
E: Broken packages
chris@ubuntu:~/Desktop$ 
```

---

### Post by slakkie on 2009-12-18
Could you enable the ppa again and redo the apt-cache policy.

I don't know how experienced you are, but you could have a look at this:

[http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

This makes sure you can mix and match your repositories so unwanted upgrades are not possible (which will prevent the unmet dependency issue for 99,9%).

I have the feeling that downgrading those packages to the normal jaunty version and then upgrading it again will fix the issue. 

Did you upgrade via apt-get upgrade/aptitude safe-upgrade or via apt-get dist-upgrade/aptitude full-upgrade?

---

