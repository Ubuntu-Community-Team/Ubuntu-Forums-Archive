---
title: "Could not download all repository indexes"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by thornside on 2007-12-12
When I try to upgrade in 7.10, through synaptic I get this message


Could not download all repository indexes
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.canonical.com/ubuntu/dists/gutsy/Release:](http://archive.canonical.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  commercial/binary-amd64/Packages in Meta-index file (malformed Release file?)


I searched but can't find an answer that has fixed this. Any help would be greatly appreciated!

---

### Post by Partyboi2 on 2007-12-13
can you post the output of this command
Open a terminal (Applications>Accessories>Terminal)
```
cat /etc/apt/sources.list
```

---

### Post by joam on 2007-12-24
**[COLOR="Red"][SIZE="4"]i have the same problem and that the output from  cat /etc/apt/sources.list[/SIZE][/COLOR]**

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

---

### Post by saspo on 2007-12-24
same problem  view screenshot.  Note that the reload button is in the synaptic manager.  It keeps asking for an internet connection.

---

### Post by Partyboi2 on 2007-12-24
> **saspo said:**
> same problem  view screenshot.  Note that the reload button is in the synaptic manager.  It keeps asking for an internet connection.
Open up "Software Sources" (System>Admin>Software Sources)
When it opens you will see under the first tab (ubuntu software) **Downloadable from the Internet**, underneath that, tick all the boxes.
then close. then try using add/remove or synaptic again to install.

---

### Post by Partyboi2 on 2007-12-25
> **joam said:**
> **[COLOR=Red][SIZE=4]i have the same problem and that the output from  cat /etc/apt/sources.list[/SIZE][/COLOR]**

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
Your source.list seems ok.  Try changing download servers and see if that helps.
Are you getting the exact same error message or something similar?

---

### Post by saspo on 2007-12-25
> **Partyboi2 said:**
> Open up "Software Sources" (System>Admin>Software Sources)
When it opens you will see under the first tab (ubuntu software) **Downloadable from the Internet**, underneath that, tick all the boxes.
then close. then try using add/remove or synaptic again to install.

You are a life saver.  I had to reinstall 7.10 and the do what you instructed.  
One question though.  What is a "root password"  I need it to install a piece of software.  I have tried my usual sign on password but that did not work.  Any help will be appreciated.

---

### Post by Partyboi2 on 2007-12-25
to install, you would put sudo in front eg
```
apt-get install vlc
```would be
```
sudo apt-get install vlc
```here is something on sudo
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
When you type your password you will not see it on screen, so make sure you are typing it correctly.
Also check that your username has Admin rights under "User Groups" (System>Admin>User Groups) click on your user name then "properties" select "user privilege" tab and make sure that "Executing system administration tasks" is checked.

---

