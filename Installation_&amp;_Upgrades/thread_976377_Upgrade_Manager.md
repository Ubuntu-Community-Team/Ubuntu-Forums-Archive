---
title: "Upgrade Manager"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by dschloyer on 2008-11-09
I am having a problem running my Update Manager.  There is an error shown that reads:

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing libwfut-0.1-0 (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Can someone advise what to do next?

Thanks much!

---

### Post by taurus on 2008-11-09
What does your /etc/apt/sources.list look like?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by dschloyer on 2008-11-10
Here is is:

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by taurus on 2008-11-10
What happens if you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dschloyer on 2008-11-11
dschloyer@dschloyer-laptop:~$ sudo apt-get update
[sudo] password for dschloyer: 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_source_Sources - open (30 Read-only file system) [IP: 91.189.88.45 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_source_Sources - open (30 Read-only file system) [IP: 91.189.88.46 80]
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_source_Sources - open (30 Read-only file system) [IP: 91.189.88.45 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_source_Sources - open (30 Read-only file system) [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock

dschloyer@dschloyer-laptop:~$ sudo apt-get update
[sudo] password for dschloyer: 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_source_Sources - open (30 Read-only file system) [IP: 91.189.88.45 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_source_Sources - open (30 Read-only file system) [IP: 91.189.88.46 80]
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_source_Sources - open (30 Read-only file system) [IP: 91.189.88.45 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.46 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_source_Sources - open (30 Read-only file system) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages - open (30 Read-only file system) [IP: 91.189.88.45 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_source_Sources - open (30 Read-only file system) [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock

Thanks for all your help!!

---

### Post by taurus on 2008-11-11
Looks like the "in" mirror site is down.  Go into System -> Administration -> Synaptic Package Manager and pick another site from the list.  You can also use the main server if you wish.  Then, save it and click refresh.  Otherwise, you can close down synaptic after you've picked another server and run those commands from a terminal again.

---

### Post by dschloyer on 2008-11-11
When I open the Synaptic Package Manager, it immediately (before allowing access to the menus) gives an error message:

E: Problem parsing dependency Depends
E: Error occurred while processing libwfut-0.1-0 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Other suggestions?

---

### Post by taurus on 2008-11-11
Close synaptic window.  I guess you just have to edit /etc/apt/sources.list by hand then.

From a terminal, run

```
gksudo gedit /etc/apt/sources.list
```
and remove the **in.** from your /etc/apt/sources.list.  Save it and close gedit editing window.  Now, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dschloyer on 2008-11-11
Perfect!  Thanks very much!!

---

### Post by deveraux on 2008-11-24
i still having problems with my update manager.  i followed the advice given to dschloyer but I don't have the same distro.  i have ubuntu 8.10 and keep getting the error message

E:Problem parsing dependency Depends, E:Error occurred while processing kbreakout (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

can you please help? i don't know what to do 

Thanks,
deveraux

---

### Post by taurus on 2008-11-24
> **deveraux said:**
> i still having problems with my update manager.  i followed the advice given to dschloyer but I don't have the same distro.  i have ubuntu 8.10 and keep getting the error message

E:Problem parsing dependency Depends, E:Error occurred while processing kbreakout (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

can you please help? i don't know what to do 

Thanks,
deveraux

Make sure you close synaptic or update manager if you have it open.  Then, open a terminal and post the complete output after you run this command.

```
sudo apt-get update
```

---

### Post by deveraux on 2008-11-24
problem solved.  apparently the mirror site was down.  so i switched to main server in software sources and went into terminal and did apt-get update.  it got the updates and the icon for new updates appeared and i clicked on it and it allowed the update to take place normally and installed them.

---

### Post by deveraux on 2008-11-24
wanted to say thanks for your help.  It is really appreciated as i am very new but willing to learn about a better system for my pc.

deveraux

---

