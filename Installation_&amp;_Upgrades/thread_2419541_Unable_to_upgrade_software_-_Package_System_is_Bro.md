---
title: "Unable to upgrade software - Package System is Broken"
date: 2019-05-23
forum: Installation &amp; Upgrades
---

### Post by Boyohazard on 2019-05-23
I am trying to upgrade my laptop from Ubuntu 18.10 to 19.04 but upon running the software updater I get an error message:

```
openjdk-8-jre: Depends: openjdk-8-jre-headless (= 8u212-b03-0ubuntu1.18.10.1) but 8u191-b12-2ubuntu0.18.10.1 is installed
```

I have tried the suggested action of disabling 3rd party repositories but as far as I can tell I wasn't using any. Upon running the command: apt-get install -f I get the following error in my terminal:

```
E: Invalid archive member header 
E: Prior errors apply to /var/cache/apt/archives/openjdk-8-jre-headless_8u212-b03-0ubuntu1.18.10.1_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
(Reading database ... 230454 files and directories currently installed.)
Preparing to unpack .../openjdk-8-jre-headless_8u212-b03-0ubuntu1.18.10.1_amd64.deb ...
Unpacking openjdk-8-jre:amd64 (8u212-b03-0ubuntu1.18.10.1) over (8u212-b03-0ubuntu1.18.10.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-3ubuntu3) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
dpkg: dependency problems prevent configuration of openjdk-8-jre:amd64:
 openjdk-8-jre:amd64 depends on openjdk-8-jre-headless (= 8u212-b03-0ubuntu1.18.10.1); however:
  Version of openjdk-8-jre-headless:amd64 on system is 8u191-b12-2ubuntu0.18.10.1.

dpkg: error processing package openjdk-8-jre:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Processing triggers for libc-bin (2.28-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 openjdk-8-jre:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have tried installing default-jdk and even tried installing the "openjdk-8-jre-headless" package from ubuntuupdates.org using xdg-open but to no avail. I get the error "Software Index is Broken" along with a suggestion to "check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list'"

But at this point I have no idea what I should be looking for

---

### Post by Rubi1200 on 2019-05-24
Hi,

please post the output of the following commands:

```
cat /etc/apt/sources.list
```

and

```
sudo dpkg --configure -a
```

Thanks.

---

### Post by Boyohazard on 2019-05-24
Thanks Rubi1200

/etc/apt/sources.list:

```
# deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ cosmic main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ cosmic main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ cosmic-updates main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ cosmic-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ cosmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ cosmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ cosmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ cosmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu cosmic-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu cosmic-security main restricted multiverse
deb http://security.ubuntu.com/ubuntu cosmic-security universe
deb-src http://security.ubuntu.com/ubuntu cosmic-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

# deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main # disabled on upgrade to bionic
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb http://gb.archive.ubuntu.com/ubuntu/ cosmic-backports main universe restricted multiverse
```

And:

```
dpkg: dependency problems prevent configuration of openjdk-8-jre:amd64:
 openjdk-8-jre:amd64 depends on openjdk-8-jre-headless (= 8u212-b03-0ubuntu1.18.10.1); however:
  Version of openjdk-8-jre-headless:amd64 on system is 8u191-b12-2ubuntu0.18.10.1.

dpkg: error processing package openjdk-8-jre:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-8-jre:amd64

```

---

### Post by Bashing-om on 2019-05-24
Boyohazard; Hey -

Saw this same issue on #ubuntu - irc- .
Do you have a virus scanner active ? If so disable the scanner and try again.

[INDENT]hope this helps
[/INDENT]

---

### Post by Boyohazard on 2019-05-24
Thanks Bashing-om but I am not running a virus scanner

---

### Post by Rubi1200 on 2019-05-24
I suggest removing then try updating again. If you really need the package you can reinstall if the upgrade goes smoothly.

```
sudo apt autoremove --purge openjdk-8-jre
```

---

### Post by Boyohazard on 2019-05-24
Thank you Rubi1200, that seems to have done the trick.

---

### Post by Boyohazard on 2019-05-24
I take it back it didn't work. The package is listed under "Security Update" when running update-manager. So even if I remove it, Ubuntu wants to download and install it again. I can opt out of the install, but is that the wisest choice given it is a "security update"?

---

### Post by Bashing-om on 2019-05-24
Boyohazard: Hummmm ...

How about we approach it like this:
```

sudo apt update
sudo apt remove --purge openjdk-8-jre-headless openjdk-8-jre
sudo apt install openjdk-8-jre
sudo apt upgrade

```

Where I expect as the headless is a dependency of openjdk-8-jre that it will install when openjdk-8-jre is installed.
If there are issues. please post back the command and the complete result. We see where we go from there.

[INDENT][INDENT]try try again :)
[/INDENT][/INDENT]

---

### Post by Boyohazard on 2019-05-24
Okay, so it seems to have solved the problem. I was able to update without issue. However, the upgrade to 19.04 aborted just before the end saying there was a problem with a package. I believe it was libvlc. So far nothing seems to be broken though and lsb_release -a returns

```
LSB Version:	core-10.2019031300ubuntu1-noarch:printing-10.2019031300ubuntu1-noarch:security-10.2019031300ubuntu1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 19.04
Release:	19.04
Codename:	disco
```

Anyway, I will mark this issue as solved I guess and start a new thread when the new problems surface lol

---

### Post by Bashing-om on 2019-05-24
Boyohazard; Great ...

Glad we got it fingered out - You do good work :)

see it is
[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Rubi1200 on 2019-05-24
> **Boyohazard said:**
> Thank you Rubi1200, that seems to have done the trick.

Sure, no problem at all.

Obviously, as I see from the following posts there were some more issues but, at least for now, they are manageable.

Good luck.

---

