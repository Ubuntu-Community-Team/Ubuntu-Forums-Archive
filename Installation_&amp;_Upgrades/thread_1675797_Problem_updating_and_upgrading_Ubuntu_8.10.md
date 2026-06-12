---
title: "Problem updating and upgrading Ubuntu 8.10"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by kbirecki on 2011-01-26
I am getting errors trying to update Ubuntu 8.1.0.  I've searched a number of sites on line and tired various suggestions that worked for other people.  I'm still a novice with Ubuntu, but I've collected the info here that I've seen other experts ask.  So if anyone can give me some feedback, I'd appreciate it.

Included below is the output I get from "sudo apt-get update", my sources.list and some network connection info.
Thanks for any suggestions that help me avoid a ground-up reinstall!

==================================================
=== This is what I get from running SUDO APT-GET UPDATE
===I get similar problems running "sudo apt-get dist-upgrade" and "sudo apt-get update -o Acquire::http::No-Cache=true" and "sudo aptitude update"
==================================================

AHI\kbirecki@methone:/var/lib/apt/lists$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
  404 Not Found [IP: 91.189.92.166 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.92.166 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.92.166 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.




==================================================
===  CONTENTS OF SOURCES.LIST
==================================================

AHI\kbirecki@methone:/etc/apt$ cat sources.list
#
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

#NOTE: "sudo apt-get update" failes wether these two lines are enabled or not.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse


==================================================
===  RESULTS OF "LSPCI"
==================================================

AHI\kbirecki@methone:/etc/apt$ lspci
00:00.0 Host bridge: Broadcom CNB20HE Host Bridge (rev 23)
00:00.1 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.2 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.3 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:04.0 Ethernet controller: 3Com Corporation 3c980-TX Fast Etherlink XL Server Adapter [Cyclone] (rev 30)
00:0e.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 50)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
01:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5700 Gigabit Ethernet (rev 10)
02:02.0 PCI bridge: Intel Corporation 80960RM (i960RM) Bridge (rev 01)
02:02.1 RAID bus controller: Dell PowerEdge Expandable RAID Controller 3/Di (rev 01)


==================================================
===  RESULTS OF "lshw -C network"
==================================================
  *-network
       description: Ethernet interface
       product: 3c980-TX Fast Etherlink XL Server Adapter [Cyclone]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 30
       serial: 00:50:04:7a:52:10
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.10.10.34 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5700 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth1
       version: 10
       serial: 00:b0:d0:f0:c4:96
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=half latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair

===================================

---

### Post by mörgæs on 2011-01-26
It is a long and risky way to upgrade to 10.04 or 10.10. The fast, safe and easy approach is a clean install.

---

### Post by kbirecki on 2011-01-26
mörgæs, I was afraid of that.  OK, that makes sense.  So I suppose the Ubuntu 7.x server in-place upgrade is out of the question, too, huh?  That's the production server I ultimately need to upgrade.  I'll plan for fresh installs.  Thanks!

---

### Post by mörgæs on 2011-01-26
If you are on Ubuntu 7, then the need for a fresh install is even bigger. There has not been security releases for 7 for a long time.

Just run a live CD before installing to verify that the new release works well and remember to have wired internet access, then you have a good start.

---

### Post by kbirecki on 2011-01-26
I have both, and that's a good suggestion about trying the Live cd first.
Thanks!

---

