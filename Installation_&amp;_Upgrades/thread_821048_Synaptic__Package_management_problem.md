---
title: "Synaptic / Package management problem"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by WarlockLord on 2008-06-06
I installed Hardy x64 a few days ago after being away from linux for a few years. I pat myself on the back for being able to get everything working as much as I have. I added a few repositories to get some software with no problems.

I opened Synaptic today and found a problem. I cannot install anything new. All my repositories are correct, but there is nothing listed under latest version for anything I haven't already installed, and when I try to install something it gives me this message for everything:

4digits:

Package 4digits has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


I guess I can't install anything new until I fix this so if someone could point me in the right direction I would appreciate it.

Thanks.

---

### Post by Pumalite on 2008-06-06
Post the output of:
sudo apt-get update

---

### Post by WarlockLord on 2008-06-06
> **Pumalite said:**
> Post the output of:
sudo apt-get update

I have since erased the extra repos for testing

tony@tony-laptop:~$ sudo apt-get update
[sudo] password for tony: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Reading package lists... Done


Actually I think I fixed it. In Synaptic I went to Preferences, then Distribution, and changed it to prefer packages from Hardy. I don't know how that option got changed, but it appears I fixed the problem. Thanks for the help!

---

### Post by Pumalite on 2008-06-06
Post:
cat /etc/apt/sources.list

---

### Post by WarlockLord on 2008-06-07
> **Pumalite said:**
> Post:
cat /etc/apt/sources.list



Synaptic works, but apt-get still gives me the same error message for every package. This is a problem because it won't let me install deb packages from the net because of unresolved dependencies.

tony@tony-laptop:~$ sudo cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
# deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) hardy main
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted

---

### Post by Pumalite on 2008-06-07
Go to System>Administration>Software Sources>Open up all your repos; including backports, updates and proposed. Exclude src unless you have a specific need for them. Then:
sudo apt-get update
sudo apt-get upgrade

---

### Post by WarlockLord on 2008-06-07
> **Pumalite said:**
> Go to System>Administration>Software Sources>Open up all your repos; including backports, updates and proposed. Exclude src unless you have a specific need for them. Then:
sudo apt-get update
sudo apt-get upgrade


Works if I install in Synaptic, apt-get gives me (for any package):

[email]tony@tony-laptop:~/.apti[/email]tude$ sudo apt-get install 3dchess
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 3dchess is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 3dchess has no installation candidate

---

### Post by Pumalite on 2008-06-07
Try soundkonverter

---

### Post by WarlockLord on 2008-06-07
> **Pumalite said:**
> Try soundkonverter

Same message

---

### Post by Pumalite on 2008-06-07
Sorry. I ran out of ideas. Someone with better ideas will come to your rescue.

---

### Post by WarlockLord on 2008-06-07
> **Pumalite said:**
> Sorry. I ran out of ideas. Someone with better ideas will come to your rescue.

I really have no idea how my little knowledge of linux helps me fix these problems. I truly am a beginner, but google can be a lot of help.

/etc/apt/preferences
Package: *
Pin: release o=Debian,a=stable
Pin-Priority: 500


needed to be:

Package: *
Pin: release o=Ubuntu,a=hardy
Pin-Priority: 500


Again, not sure how it got changed but it did fix my problem. Back on track!

---

