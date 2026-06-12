---
title: "installed rpm support by misstake"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by hazze on 2006-12-12
Hello!

I have by misstake installed rpm support and now I can't install .deb packages. And for what I know synaptic uses deb packages, because synaptic doesent work either.

So how to uninstall or modify so i can use .deb and synaptic?

---

### Post by ciscosurfer on 2006-12-12
Installing RPM support should not prevent you from using Synaptic (uses apt and dpkg).

Can you tell me what you installed?

You can try this to get things working again```
sudo aptitude update && sudo aptitude install apt dpkg synaptic
```

---

### Post by dalonso on 2006-12-12
> **hazze said:**
> Hello!

I have by misstake installed rpm support and now I can't install .deb packages. And for what I know synaptic uses deb packages, because synaptic doesent work either.

So how to uninstall or modify so i can use .deb and synaptic?

Don't worry at all. Installing rpm support has no effect in synaptic. So surely you are having a different problem not related to rpm support installation.

What's the error that synaptic returns you? Can you run synaptic within a shell and tell us what messages are being printed?

---

### Post by hazze on 2006-12-12
Synaptic works but it doesn't show any packages...

When "sudo apt-get update" I get:

E: Package dcp540cncupswrapper must be reinstalled, but I cant find any achive for it.

(Translated from swedish error message :D)

this is a printer driver which i tried to install at the same time i installed the rpm packages....

---

### Post by ciscosurfer on 2006-12-12
A printer driver will also have no effect on using Apt.

Again, though, to reinsall CUPS you would issue```
sudo aptitude install cups
```What else have you modified?

Can you please post your /etc/apt/sources.list```
cat /etc/apt/sources.list
```

---

### Post by hazze on 2006-12-12
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy main restricted


## Major bug fix updates produced after the final release of the

## distribution.

# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-updates main restricted


## Uncomment the following two lines to add software from the 'universe'

## repository.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


## Add comments (##) in front of any line to remove it from being checked.   

## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse


## MAJOR BUG FIX UPDATES produced after the final release

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse


## UBUNTU SECURITY UPDATES

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)

deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
                                                                                                                                         

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu

## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


## Listen

# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen


#Beryl

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy


# Repository for wine

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


#Commercial

# deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) edgy-commercial main
# deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main

#NTFS support for removable disks
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main

---

### Post by ciscosurfer on 2006-12-12
You sources.list looks fine (the entries that you are trying to load should load just fine).  You may neee to check your GPG signatures and make sure they coincide with what you are trying to download.  You need to make sure that you have reinstalled apt, dpkg, and synaptic.  Having rpm support won't change your ability to download .deb packages or source files.  I assume you reinstalled CUPS, but that again, would have no effect.  One last try: can download .debs from Web, and then install them manually?

I'm sorry, but I don't know how to help you with your problem anymore.  

Perhaps someone else knows the answer to hazze's problem?

---

### Post by hazze on 2006-12-13
Okey... No i can't download and install .deb... "Archivetype is not supported" 


Thanks for the help so far... but nothing seem to work..

---

### Post by ciscosurfer on 2006-12-13
If you install is fairly new and you don't have many personal files that you don't mind backing up, then I would suggest a fresh install of either Dapper or Edgy (whichever you are more comfortable with)...this will certainly fix the problem.  ***I realize this isn't ideal***, but without knowing more about exactly what you removed, it's very hard to determine the course of action.  Try to run through the steps that I provided above first and then maybe go ahead with a reinstall.

---

### Post by hazze on 2006-12-13
These are the packages that I installed on the day synaptic stoped working


rpm (4.4.1-9.1ubuntu0.1)

python-rpm (4.4.1-9.1ubuntu0.1)
smartpm (0.42-0ubuntu2)
smartpm-core (0.42-0ubuntu2)

libbeecrypt6 (4.1.2-5)
librpm4 (4.4.1-9.1ubuntu0.1)

---

### Post by hazze on 2006-12-13
Reinstall is no option =)... I have lots of files and configuration I can't loose

---

### Post by ciscosurfer on 2006-12-13
> **hazze said:**
> These are the packages that I installed on the day synaptic stoped working


rpm (4.4.1-9.1ubuntu0.1)

python-rpm (4.4.1-9.1ubuntu0.1)
smartpm (0.42-0ubuntu2)
smartpm-core (0.42-0ubuntu2)

libbeecrypt6 (4.1.2-5)
librpm4 (4.4.1-9.1ubuntu0.1)Can you remove those packages?  Then try to reinstall apt, dpkg, synaptic?  Again, installing those shouldn't have had any adverse effects...

---

