---
title: "Upgrade from 19.10 to 20.04"
date: 2023-08-22
forum: Installation &amp; Upgrades
---

### Post by kraf101 on 2023-08-22
Hi
I failed to upgrade on time and now must to upgrade via 20.04 release. 
I replaced source.list with old-releases. 
do-release-upgrade -c shows "20.04.5 LTS"
then during upgrade, a lot of errors like:
> Error: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 pulseaudio amd64 1:13.99.1-1ubuntu3.13
.... /var/cache/apt/archives/partial/pulseaudio_1%3a13.99.1-1ubuntu3.13_amd64.deb - open (13: No access) [IP: 153.19.251.225 80]

Is there any trick to upgrade it?

---

### Post by readableauthor on 2023-08-22
Did you do this before updating:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by kraf101 on 2023-08-22
> **readableauthor said:**
> Did you do this before updating:
```

sudo apt-get update
sudo apt-get upgrade

```
Yes.

---

### Post by Rubi1200 on 2023-08-22
Please post the output of this:
```
cat /etc/apt/sources.list
```

and also

```
cat /etc/apt/sources.list.d
```

When replying using Go Advanced and wrap the text using # tags please

---

### Post by kraf101 on 2023-08-22
> **Rubi1200 said:**
> Please post the output of this:
When replying using Go Advanced and wrap the text using # tags please
cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017)]/ eoan main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://old-releases.ubuntu.com/ubuntu/ eoan main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu/ eoan main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ eoan-updates main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu/ eoan-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ eoan universe
# deb-src http://old-releases.ubuntu.com/ubuntu/ eoan universe
deb http://old-releases.ubuntu.com/ubuntu/ eoan-updates universe
# deb-src http://old-releases.ubuntu.com/ubuntu/ eoan-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ eoan multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ eoan multiverse
deb http://old-releases.ubuntu.com/ubuntu/ eoan-updates multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ eoan-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu eoan partner
# deb-src http://archive.canonical.com/ubuntu eoan partner

deb http://old-releases.ubuntu.com/ubuntu eoan-security main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu eoan-security main restricted
deb http://old-releases.ubuntu.com/ubuntu eoan-security universe
# deb-src http://old-releases.ubuntu.com/ubuntu eoan-security universe
deb http://old-releases.ubuntu.com/ubuntu eoan-security multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu eoan-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
deb http://archive.ubuntu.com/ubuntu trusty universe
# deb-src http://archive.ubuntu.com/ubuntu trusty universe
# deb [arch=amd64] https://download.docker.com/linux/ubuntu eoan stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu eoan stable

```

/etc/apt/sources.list.d is a directory, then:

ls /etc/apt/sources.list.d
```
pgadmin4.list  pgadmin4.list.distUpgrade

```

---

### Post by Rubi1200 on 2023-08-22
The sources list shows you still have for 19.10, which is EOL.

Any reason not to upgrade to the latest LTS?

If it was me, I would recommend backing everything up and doing a clean install of 22.04.

Anyway, I have seen enough instances when people tried upgrading via interim releases and it just went wrong, for many reasons.

---

### Post by kraf101 on 2023-08-22
> **Rubi1200 said:**
> The sources list shows you still have for 19.10, which is EOL.

Any reason not to upgrade to the latest LTS?

If it was me, I would recommend backing everything up and doing a clean install of 22.04.

20.04 is an LTS release, not an interim one.
For practical reasons, I try to avoid a complete installation.
The server is somewhere else, so I'll have to go there, connect the display, keyboard, etc. Also, quite a few users are settled there. So first thought, to try to do it from the desk.

---

### Post by TheFu on 2023-08-22
> **kraf101 said:**
> 20.04 is an LTS release, not an interim one.
For practical reasons, I try to avoid a complete installation.
The server is somewhere else, so I'll have to go there, connect the display, keyboard, etc. Also, quite a few users are settled there. So first thought, to try to do it from the desk.

Seems like you need to find your car keys.
I do 1 upgrade from LTS --> LTS, then a fresh install for the 2nd LTS upgrade.  Repeat.  Basically, every other LTS install is fresh.  I don't touch non-LTS releases except for playing around, never for production.

if there's a plane involved to get there, might be best to spend $260 to get a pikvm device and have someone there hook it up. [https://pikvm.org/](https://pikvm.org/). It is like a networked KVM switch. Of course, if the remote system is a real server, you can use IPMI and just need someone to plug in a new USB flash drive to boot with the 22.04 OS on it.

Learn from this.  Next time, do the upgrade BEFORE support ends.  However, I've had some upgrades fail after running over 2 hrs.  In the end, it was more efficient to just perform a fresh install, then restore data, settings, and list of packages from backups.  That takes less than 45min for most of my systems. Some, those without any data with just services, can be setup using the restore in about 20 min.    10-15min is for a fresh OS install.

---

