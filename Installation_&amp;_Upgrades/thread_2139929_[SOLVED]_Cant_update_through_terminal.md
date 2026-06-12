---
title: "[SOLVED] Cant update through terminal?"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by demonic_crow on 2013-04-28
I upgraded my laptop from Ubuntu 10.04 to Ubuntu 12.04 on my laptop.  It is a 64bit computer. When I run **sudo apt-get update** I get an error.

```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

The result of the etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe #Added by software-properties
# deb http://ubuntusatanic.org/hell precise main # disabled on upgrade to precise
# deb http://badgerports.org precise main # disabled on upgrade to precise
```

What am I'm needing to do to fix this. I don't see any i386 or 64 bit mention above.

---

### Post by ibjsb4 on 2013-04-28
Looking in the wrong place :) var/lib/apt/lists

The easy fix:

[http://ubuntuforums.org/showthread.php?t=2131178&p=12583395&viewfull=1#post12583395](http://ubuntuforums.org/showthread.php?t=2131178&p=12583395&viewfull=1#post12583395)

---

### Post by demonic_crow on 2013-04-28
I enter those 3 lines and I'm still having the same error coming up. Should I just go to **var/lib/apt/lists **and delete the i386 files that are located there?

---

### Post by Elfy on 2013-04-28
> **demonic_crow said:**
> sudo: rm-r: command not found

When you are copying rm commands it is very important you get them right, in the case you've got 'command not found' you might have got nothing and found you'd made an error.

As it is the command is 

```
sudo rm -r /var/lib/apt/lists/*
```

not

```
sudo rm-r /var/lib/apt/lists/*
```

---

### Post by demonic_crow on 2013-04-28
> **Elfy said:**
> When you are copying rm commands it is very important you get them right, in the case you've got 'command not found' you might have got nothing and found you'd made an error.

As it is the command is 

```
sudo rm -r /var/lib/apt/lists/*
```

not

```
sudo rm-r /var/lib/apt/lists/*
```

Thanks, I realize my mistake and thats why I edited my post. I'm still having the issue though even after I posted all three lines.

---

### Post by gordintoronto on 2013-04-28
You're getting warning messages, it should not stop anything. Did you run:
sudo apt-get update
as was suggested?

---

### Post by demonic_crow on 2013-05-01
> **gordintoronto said:**
> You're getting warning messages, it should not stop anything. Did you run:
sudo apt-get update
as was suggested?

Yes I did do that. Should I look in the **/var/lib/apt/lists** and delete anyting that says i386?

---

### Post by matt_symes on 2013-05-01
Hi

Can we check all you sources including PPAs.

Please post the output of this command

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by demonic_crow on 2013-05-01
```
/etc/apt/sources.list:2:deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties
/etc/apt/sources.list:6:deb http://archive.ubuntu.com/ubuntu precise main restricted
/etc/apt/sources.list:7:deb-src http://archive.ubuntu.com/ubuntu precise multiverse universe #Added by software-properties
/etc/apt/sources.list:11:deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
/etc/apt/sources.list:12:deb-src http://archive.ubuntu.com/ubuntu precise-updates restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:17:deb http://archive.ubuntu.com/ubuntu precise universe
/etc/apt/sources.list:18:deb http://archive.ubuntu.com/ubuntu precise-updates universe
/etc/apt/sources.list:25:deb http://archive.ubuntu.com/ubuntu precise multiverse
/etc/apt/sources.list:26:deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
/etc/apt/sources.list:35:deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
/etc/apt/sources.list:36:deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse #Added by software-properties
/etc/apt/sources.list:42:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:43:deb-src http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:45:deb http://archive.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:46:deb-src http://archive.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:47:deb http://archive.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:48:deb http://archive.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:49:deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
/etc/apt/sources.list:50:deb-src http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list.d/aheck-ppa-lucid.list.distUpgrade:1:deb http://ppa.launchpad.net/aheck/ppa/ubuntu lucid main
/etc/apt/sources.list.d/aheck-ppa-lucid.list.save:1:deb http://ppa.launchpad.net/aheck/ppa/ubuntu lucid main
/etc/apt/sources.list.d/cheleb-blender-svn-lucid.list.save:1:deb http://ppa.launchpad.net/cheleb/blender-svn/ubuntu lucid main
/etc/apt/sources.list.d/chrysn-openscad-lucid.list.distUpgrade:1:deb http://ppa.launchpad.net/chrysn/openscad/ubuntu lucid main
/etc/apt/sources.list.d/chrysn-openscad-lucid.list.save:1:deb http://ppa.launchpad.net/chrysn/openscad/ubuntu lucid main
/etc/apt/sources.list.d/dropbox.list.distUpgrade:1:deb http://linux.dropbox.com/ubuntu lucid main
/etc/apt/sources.list.d/dropbox.list.save:1:deb http://linux.dropbox.com/ubuntu lucid main
/etc/apt/sources.list.d/freecad-maintainers-freecad-daily-lucid.list.distUpgrade:1:deb http://ppa.launchpad.net/freecad-maintainers/freecad-daily/ubuntu lucid main
/etc/apt/sources.list.d/freecad-maintainers-freecad-daily-lucid.list.save:1:deb http://ppa.launchpad.net/freecad-maintainers/freecad-daily/ubuntu lucid main
/etc/apt/sources.list.d/google-chrome.list:3:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:3:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:3:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/linuxcnc.list.distUpgrade:1:deb http://www.linuxcnc.org/emc2 lucid base emc2.4
/etc/apt/sources.list.d/linuxcnc.list.distUpgrade:2:deb-src http://www.linuxcnc.org/emc2 lucid base emc2.4
/etc/apt/sources.list.d/linuxcnc.list.save:1:deb http://www.linuxcnc.org/emc2 lucid base emc2.4
/etc/apt/sources.list.d/linuxcnc.list.save:2:deb-src http://www.linuxcnc.org/emc2 lucid base emc2.4
/etc/apt/sources.list.d/lucid-partner.list:4:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list.d/lucid-partner.list.distUpgrade:4:deb http://archive.canonical.com/ubuntu lucid partner
/etc/apt/sources.list.d/lucid-partner.list.save:4:deb http://archive.canonical.com/ubuntu lucid partner
/etc/apt/sources.list.d/paxer-ppa-lucid.list.distUpgrade:1:deb http://ppa.launchpad.net/paxer/ppa/ubuntu lucid main
/etc/apt/sources.list.d/paxer-ppa-lucid.list.save:1:deb http://ppa.launchpad.net/paxer/ppa/ubuntu lucid main

```

---

### Post by matt_symes on 2013-05-01
Hi

> /etc/apt/sources.list:42:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

/etc/apt/sources.list.d/lucid-partner.list:4:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

You have duplicate sources on your system. We need to get rid one of them.

From the terminal...

```
sudo rm /etc/apt/sources.list.d/lucid-partner.list
```

```
sudo rm -rf /var/lib/apt/lists/*
```

```
sudo mkdir /var/lib/apt/lists/partial
```

```
sudo apt-get update
```

Kind regards

---

### Post by demonic_crow on 2013-05-01
Thank you, it updated just fine for me

---

