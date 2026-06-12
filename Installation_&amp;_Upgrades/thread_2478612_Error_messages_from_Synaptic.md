---
title: "Error messages from Synaptic"
date: 2022-08-30
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2022-08-30
A couple days go I did the dist-upgrade from 20.04.x to 22.04.1, which went more or less OK. While fixing things I've needed to do a few reinstalls and new installs, and I keep getting a popup:

> W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:33


I tried reloading in Synaptic, but got the same list of errors. Ditto for 'sudo apt update' at the command line. I need some suggestions.

---

### Post by Bashing-om on 2022-08-30
Hey  John Jason Jordan --

The system is telling you that there are duplications in the source get file. One of the entries needs to be removed.
see from terminal:
```

cat -n /etc/apt/sources.list

```
 Here I expect you will see that line 4 and line 33 are the same.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by John Jason Jordan on 2022-08-31
> **Bashing-om said:**
> Hey  John Jason Jordan --
The system is telling you that there are duplications in the source get file. One of the entries needs to be removed.
see from terminal:
```

cat -n /etc/apt/sources.list

```
 Here I expect you will see that line 4 and line 33 are the same.
[/INDENT]

Thanks for the suggestion. Unfortunately, /etc/apt/sources.list doesn't even have 33 lines. There are only about a dozen that aren't commented out:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy restricted main multiverse universe #Added by software-properties
## Major bug fix updates produced after the final release of the
## distribution.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [arch=amd64] [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) focal contrib # disabled on upgrade to focal
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main restricted # auto generated by ubuntu-release-upgrader
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe main restricted multiverse # auto generated by ubuntu-release-upgrader
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy main restricted # auto generated by ubuntu-release-upgrader
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates main restricted universe multiverse # auto generated by ubuntu-release-upgrader
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security main restricted # auto generated by ubuntu-release-upgrader

While poking around I noticed that the upgrade disabled all of my PPAs. This means that I won't get updates on a lot of programs that I use all the time. I haven't re-enabled them; waiting until I get this problem solved.

---

### Post by deadflowr on 2022-08-31
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
**deb http://archive.ubuntu.com/ubuntu jammy main restricted**
deb-src http://archive.ubuntu.com/ubuntu jammy restricted main multiverse universe #Added by software-properties
## Major bug fix updates produced after the final release of the
## distribution.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu jammy universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu jammy multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib # disabled on upgrade to focal
# deb http://archive.ubuntu.com/ubuntu focal main restricted # auto generated by ubuntu-release-upgrader
deb http://security.ubuntu.com/ubuntu jammy-security universe main restricted multiverse # auto generated by ubuntu-release-upgrader
**deb http://archive.ubuntu.com/ubuntu jammy main restricted** # auto generated by ubuntu-release-upgrader
deb http://archive.ubuntu.com/ubuntu jammy-updates main restricted universe multiverse # auto generated by ubuntu-release-upgrader
deb http://security.ubuntu.com/ubuntu jammy-security main restricted # auto generated by ubuntu-release-upgrader
```

I've highlighted in bold the entries that are the same.
Remove one of them.

---

### Post by ajgreeny on 2022-08-31
The version upgrade will always disable all PPAs as there would be problems if they remained enabled.

This is completely expected and the upgrade instructions suggest PPAs are deleted before version upgrades. You may find some of those you used are no longer needed so check before you add them back.

---

