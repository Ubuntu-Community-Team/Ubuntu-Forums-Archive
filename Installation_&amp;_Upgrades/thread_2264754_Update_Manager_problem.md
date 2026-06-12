---
title: "Update Manager problem"
date: 2015-02-09
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2015-02-09
Folks,

I am still running 12.04.4 LTS. I downloaded xubuntu 14.04.1 iso and from it created a disk. However, since downloading xubuntu, there appears to be a problem with Update Manager.

Initially, when I select to download the updates a message displays telling me to place the xubuntu disk into my CD slot. When I've done this, I select the dialog button 'Continue' but all that happens is the same message displays. I then select the Cancel button and the updates seem download. 

When I try to install them under Update Manager, I get the following message:

Failed to download package files
Check your internet connection
Clicking the Details down arrow gives the following:
Filed to fetch cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/pool/main/f/fakeroot/fakeroot_1.20-3ubuntu2_amd64.deb Unable to stat the mount point /media/cdrom/ - stat (2: No such file or directory)
Failed to fetch cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/pool/main/f/fakeroot/libfakeroot_1.20-3ubuntu2_amd64.deb File not found

My internet connection is working perfectly, so that isn't the problem.

On reopening the Update Manager, the updates are still shown, and the message:
7 updates hve been selected. The updates have already been downloaded, but not installed.

Can anyone tell me what is causing the problem, any help gratefully accepted.

Regards,
Bob

---

### Post by sandyd on 2015-02-09
> **bobmac said:**
> Folks,

I am still running 12.04.4 LTS. I downloaded xubuntu 14.04.1 iso and from it created a disk. However, since downloading xubuntu, there appears to be a problem with Update Manager.

Initially, when I select to download the updates a message displays telling me to place the xubuntu disk into my CD slot. When I've done this, I select the dialog button 'Continue' but all that happens is the same message displays. I then select the Cancel button and the updates seem download. 

When I try to install them under Update Manager, I get the following message:

Failed to download package files
Check your internet connection
Clicking the Details down arrow gives the following:
Filed to fetch cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/pool/main/f/fakeroot/fakeroot_1.20-3ubuntu2_amd64.deb Unable to stat the mount point /media/cdrom/ - stat (2: No such file or directory)
Failed to fetch cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/pool/main/f/fakeroot/libfakeroot_1.20-3ubuntu2_amd64.deb File not found

My internet connection is working perfectly, so that isn't the problem.

On reopening the Update Manager, the updates are still shown, and the message:
7 updates hve been selected. The updates have already been downloaded, but not installed.

Can anyone tell me what is causing the problem, any help gratefully accepted.

Regards,
Bob

Hi, can you post the output of
```

cat /etc/apt/sources.list
```

Thanks!

---

### Post by bobmac on 2015-02-09
Sandyd,

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/main/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/multiverse/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/restricted/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/universe/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) precise main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) precise main

---

### Post by fantab on 2015-02-09
Do you Ubuntu 12.04 or Xubuntu?

Why didn't you upgrade from update-manager to 14.04 and downloaded the iso?

You /etc/apt/sources.list seems to have changed.
Post the output of:
```
cat /etc/apt/sources.list
```

Since you want to upgrade to 1404 anyway and have downloaded the .iso, you can 'burn' it to DVD/USB and you can either upgrade or do a clean install. I'd recommend clean install.
If you have /home on a separate partition you can keep it by choosing NOT to format your /home during install...
... and if you don't then Backup you data, preferably externally, and think about keeping your data on a separate partition and system files on a separate partition.

---

### Post by bobmac on 2015-02-10
I didn't download 14.04 from the Update Manager because when I attempt to do so i get a message that tells me that my graphics are incompatible with the new version

Bob

---

### Post by bobmac on 2015-02-10
Folks,

When I rebooted my system, the Update Manager informed me that there were updates. When I selected to download them the following message displayed:

CD/DVD 'Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)' is required

Please insert the above CD/DVD into the drive '/media/cdrom/' to install software packages from it.

I Inserted the xubuntu disk in  the cd drive and selected the Continue button from the dialog. All that occurred was that the message redisplayed.

Bob

---

### Post by plucky on 2015-02-10
> deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/main/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/multiverse/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/restricted/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ dists/trusty/universe/binary-i386/
deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe

Your Xubuntu 14.04.1 CD has been added to your Software Sources which causes > Filed to fetch cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/pool/main/f/fakeroot/fakeroot_1.20-3ubuntu2_amd64.deb Unable to stat the mount point /media/cdrom/ - stat (2: No such file or directory)
Failed to fetch cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/pool/main/f/fakeroot/libfakeroot_1.20-3ubuntu2_amd64.deb File not found

Remove the entries from your Software Sources and then run ```
sudo apt-get update
``` to see if you get the same error.
> I didn't download 14.04 from the Update Manager because when I attempt to do so i get a message that tells me that my graphics are incompatible with the new version


You will probably need to do a fresh install of Xubuntu 14.04.1 if your machine will not support Ubuntu 14.04
Some older machines are not able to run Ubuntu 14.04 as it uses Compiz and 2D mode in 12.04 is not available in 14.04.

I don't think you can upgrade from Ubuntu 12.04 to Xubuntu 14.04 (But I could be wrong)

Good Luck

---

### Post by bobmac on 2015-02-10
Plucky et al,

Plucky, your info worked a treat.

Many thanks to all who provided information.

Regards,

Bob

---

