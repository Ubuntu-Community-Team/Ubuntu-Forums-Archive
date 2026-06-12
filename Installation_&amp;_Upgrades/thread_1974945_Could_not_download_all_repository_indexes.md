---
title: "Could not download all repository indexes"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by eldafani on 2012-05-06
Hi all,

I can't update Ubuntu 10.04 LTS. The update manager says:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://mirrors.softliste.de](http://mirrors.softliste.de) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

Any ideas on how to fix this? Many thanks,
Daniel

---

### Post by zvacet on 2012-05-07
In **synaptic>repositories** try to change server and see it that work.

---

### Post by eldafani on 2012-05-07
I changed the server in synaptic-settings-repositories-download from. And still, I got the following error message:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)GPG error: [http://mirrors.softliste.de](http://mirrors.softliste.de) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas? Thanks.

---

### Post by raja.genupula on 2012-05-07
check your source list , you could have two same source lines , delete any one of them . and try again .

---

### Post by eldafani on 2012-05-07
Not so sure if I understand. But the file /etc/apt/sources.lists does not seem to have duplicates, it is posted below:

deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid universe
deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid multiverse
deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid-security main restricted
deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid-security universe
deb [http://ubuntuarchive.eweka.nl/ubuntu/](http://ubuntuarchive.eweka.nl/ubuntu/) lucid-security multiverse
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) lucid main ## Cairo-Dock-PPA-Stable
deb [http://mirrors.softliste.de/cran/bin/linux/ubuntu](http://mirrors.softliste.de/cran/bin/linux/ubuntu) lucid/

---

### Post by raja.genupula on 2012-05-07
ok open your terminal do this```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```


let us know what you got .

---

### Post by eldafani on 2012-05-07
Now I get:

Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by eldafani on 2012-05-07
Sorry, that I get in the update manager, in the terminal the message reads:


E: Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by hijacker777 on 2012-05-07
> **raja.genupula said:**
> ok open your terminal do this```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```


let us know what you got .

This solve the issue for me, thx.

---

### Post by hijacker777 on 2012-05-07
> **eldafani said:**
> Sorry, that I get in the update manager, in the terminal the message reads:


E: Lists directory /var/lib/apt/lists/partial is missing.

Pleae try this:

```
sudo mkdir /var/lib/apt/lists/partial
```

---

### Post by eldafani on 2012-05-07
Thanks. But still I can't update with the manager. The message is:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://mirrors.softliste.de](http://mirrors.softliste.de) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

