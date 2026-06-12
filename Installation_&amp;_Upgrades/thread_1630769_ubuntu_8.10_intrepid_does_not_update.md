---
title: "ubuntu 8.10 intrepid does not update"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by NathanAdler on 2010-11-25
Hi,

Can someone help me on this? I am some kind of a beginner... I will appreciate a good advice on what to do.. Thanks a lot beforehand.

I am afraid that some big update or upgrade can spoil my configuration files or critical applications like apache or mysql...

Anyhow I haven't been able to update my system...

Everytime I try to do: "sudo apt-get update" I get these messages:

[FONT=Courier New][SIZE=1]Ign http://co.archive.ubuntu.com intrepid-updates/restricted Translation-es
Err http://security.ubuntu.com intrepid-security/main Packages
  404 Not Found
W: Imposible obtener http://co.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-amd64/Packages.gz  404 Not Found
E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

[/SIZE][/FONT]I have this OS:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

This is the /etc/apt/sources.list that I have:

[FONT=Courier New][SIZE=1]# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://co.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://co.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://co.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://co.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://co.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://co.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://co.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://co.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://co.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://co.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://co.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://co.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://co.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://co.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse[/SIZE][/FONT]


Nathan,
Colombia

---

### Post by davidmohammed on 2010-11-25
intrepid is no longer supported.  I would recommend you backup what you need and do a fresh install of lucid (10.04).

---

### Post by NathanAdler on 2010-11-25
Thanks a lot David,

In the meantime I haven't been able... not even installing new software... Why? The fact that this distro is not supported anymore shouldn't mean that I cannot install new software, should it?

Is there some steps recipe that I need to follow in order to do this process or is is just a matter of backing up and install?


Nathan.

---

### Post by davidmohammed on 2010-11-26
I cant find the intrepid repositories - so I would surmise they are no longer available - hence you cannot do any software upgrades via synaptic manager or update manager.  The only way you can keep intrepid going is to download the source files and compile up and install from them.

I would slot in an external hard-drive or USB drive.  Copy the files and folders you need to backup.  Look out for the apache config files (I dont know myself where they are kept) and back that up.

Then just install over you intrepid installation choosing the "erase the hard-drive" option when prompted during partitioning.

Install whatever you need and copy back the configs and files that you previously backed up.

---

### Post by ezsit on 2010-11-26
EOL Upgrades help page:

[https://help.ubuntu.com/community/EOLUpgrades?action=show&redirect=IntrepidUpgrades](https://help.ubuntu.com/community/EOLUpgrades?action=show&redirect=IntrepidUpgrades)

---

### Post by cubicerp on 2011-07-18
Change the /etc/apt/sources.list to:
 
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

Best Regards

---

### Post by scotty581 on 2012-02-15
> **cubicerp said:**
> Change the /etc/apt/sources.list to:
 
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

Best Regards

This is the fix for this issue.:popcorn:

---

### Post by oldos2er on 2012-02-16
Closed, necromancy.

---

