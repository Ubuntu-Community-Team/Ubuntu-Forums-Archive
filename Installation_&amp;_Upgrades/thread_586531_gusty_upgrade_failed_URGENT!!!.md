---
title: "gusty upgrade failed URGENT!!!"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by underdog512 on 2007-10-22
my resent attempt to upgrade to gutsy via internet failed.  I got past fetching the files however right in the middle upgrading it suddenly said "failed to upgrade" indicating some package which  I neglected to write down.  the upgrade tool terminated all together after this error message leaving my system virtually half upgraded.  

My question is what should I do at this point.  Should i just restart the upgrade process?  Is my system screwed now?  by the way I have not rebooted my system since the failure.

---

### Post by ThrobbingBrain66 on 2007-10-22
As long as you havent rebooted, you should be fine.  First I'll need you to post your sources.list here so we can make sure everything is ship-shape.
```
 cat /etc/apt/sources.list
```

---

### Post by Sef on 2007-10-22
Do you have any nonstandard packages installed (e.g. automatix, video card drivers, etc?)

---

### Post by Ice_man^^ on 2007-10-22
I'm having problems whit the upgrade too.When the upgrade begins i recieve this message :

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
:(
I've uninstalled my wine but nothing changes .Automatix is still installed on my system what shoud I do ???  :confused:

---

### Post by Toshick on 2007-10-22
I have the same problem. I've tried to change sources urls. But anyway i have error that update manager can't download some files and every time files are different! I have amd64 release. Maybe not all mirrors already up-to-date? Can you recommend 100% live  up-to-date mirror?
Last time i have this errors:
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/feisty/Release](http://ftp.osuosl.org/pub/ubuntu/dists/feisty/Release) Unable to find expected entry  restrictred/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/universe/binary-amd64/Packages.gz](http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/multiverse/binary-amd64/Packages.gz](http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/main/restricted/source/Sources.gz](http://ftp.osuosl.org/pub/ubuntu/dists/main/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/main/universe/source/Sources.gz](http://ftp.osuosl.org/pub/ubuntu/dists/main/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/main/multiverse/source/Sources.gz](http://ftp.osuosl.org/pub/ubuntu/dists/main/multiverse/source/Sources.gz) 404 Not Found

---

### Post by ThrobbingBrain66 on 2007-10-22
> **Ice_man^^ said:**
> I'm having problems whit the upgrade too.When the upgrade begins i recieve this message :

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
:(
I've uninstalled my wine but nothing changes .Automatix is still installed on my system what shoud I do ???  :confused:

You may have uninstalled Wine, but you need to remove the repo from your sources.list file.  Use the following command to open the file and then delete** any and all 3rd party repos**.  Automatix should be removed as well.
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by ThrobbingBrain66 on 2007-10-22
> **Toshick said:**
> I have the same problem. I've tried to change sources urls. But anyway i have error that update manager can't download some files and every time files are different! I have amd64 release. Maybe not all mirrors already up-to-date? Can you recommend 100% live  up-to-date mirror?
Last time i have this errors:
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/feisty/Release](http://ftp.osuosl.org/pub/ubuntu/dists/feisty/Release) Unable to find expected entry  restrictred/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/universe/binary-amd64/Packages.gz](http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/multiverse/binary-amd64/Packages.gz](http://ftp.osuosl.org/pub/ubuntumain/dists/restricted/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/main/restricted/source/Sources.gz](http://ftp.osuosl.org/pub/ubuntu/dists/main/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/main/universe/source/Sources.gz](http://ftp.osuosl.org/pub/ubuntu/dists/main/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ftp.osuosl.org/pub/ubuntu/dists/main/multiverse/source/Sources.gz](http://ftp.osuosl.org/pub/ubuntu/dists/main/multiverse/source/Sources.gz) 404 Not Found

Try to use the local mirror for your country.  You can access your download mirror by going to System > Administration > Software Sources.

To Ice_man and Toshik: try not to hijack other's threads.  It leads to confusion.  If you have a problem, either wait for a similar thread to be solved or create your own.

---

### Post by underdog512 on 2007-10-22
> **ThrobbingBrain66 said:**
> As long as you havent rebooted, you should be fine.  First I'll need you to post your sources.list here so we can make sure everything is ship-shape.
```
 cat /etc/apt/sources.list
```

Here is my sources file as requested.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## Medibuntu - Ubuntu 6.10 “feisty”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)

##MediaTomb
# deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main

# deb [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) gutsy screenlets

---

### Post by underdog512 on 2007-10-23
somebody please advise as to what to do next!

---

### Post by ThrobbingBrain66 on 2007-10-23
Your sources.list looks good.  Since your sources.list already reflects gutsy, try running:

```
sudo aptitude full-upgrade
sudo dpkg --configure -a
```

---

### Post by underdog512 on 2007-10-23
update manager says that my system is up-to-date.  should I just mark all upgrades in synaptic?

---

### Post by ThrobbingBrain66 on 2007-10-23
When you ran update-manager, did you use the '-d' option?

```
gksudo update-manager -d
```

---

### Post by underdog512 on 2007-10-23
> **ThrobbingBrain66 said:**
> Your sources.list looks good.  Since your sources.list already reflects gutsy, try running:

```
sudo aptitude full-upgrade
sudo dpkg --configure -a
```


I did this but I forgot to run the dpkg --configure - a before I restarted now my graphics card has not been detected I am running in low graphics mode what shall I do now?

---

### Post by ThrobbingBrain66 on 2007-10-23
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions to the best of your ability.  If you don't know the answer to any questions, just accept the default.

After that, make sure to run the following commands to make sure everything has been upgraded/configured and all dependencies are satisfied:

```

sudo dpkg --configure -a
sudo apt-get install -f
sudo aptitude full-upgrade
sudo aptitude safe-upgrade

```

---

### Post by NoxioiusWarrior on 2007-10-26
Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found


Here are the errors I receive when i try to upgrade....any help would be appreciated..

---

### Post by mwacky on 2007-11-01
Edit your /etc/apt/sources.list file and remove comment out your medibuntu packages and any others that are 3rd Party.

---

