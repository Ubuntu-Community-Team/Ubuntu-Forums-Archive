---
title: "Disabled Repositories"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by GNUway Tech on 2012-10-20
I have this problem every time I upgrade to a newer version. I just upgraded to 12.10, and the upgrade disabled some of my repos. I tried to enable them by just rechecking them in Software Sources, but it's still not reading them. How do I enable them???

---

### Post by dino99 on 2012-10-20
update the sources.list:

sudo gedit /etc/apt/sources.list

then : sudo apt-get update

---

### Post by GNUway Tech on 2012-10-21
I can see the command for the sources list, but how do I update it????

---

### Post by varunendra on 2012-10-21
The most common reasons are broked/dead ppa links, incompatible version, etc.

What *dino* meant, I think, was to check and correct them manually (by following the links and/or correcting the versions from 'precise' to 'quantal'), then do an 'sudo apt-get update'. If not sure how to do this, please post the contents of your 'sources.list' file :
```
cat /etc/apt/sources.list
```

---

### Post by GNUway Tech on 2012-10-21
Here's the list file

> # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe #Added by software-properties
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main


---

### Post by DustofDust on 2012-10-22
add [https://launchpad.net/~webupd8team/+archive/y-ppa-manager](https://launchpad.net/~webupd8team/+archive/y-ppa-manager) to your lists of repos with synaptics... if you dont have synaptics installed do it as its easier to change things like repos

[http://www.webupd8.org/2012/10/y-ppa-manager-0092-released-with-new.html](http://www.webupd8.org/2012/10/y-ppa-manager-0092-released-with-new.html)
you can also follow this way to install

> - Re-enable working PPAs after Ubuntu upgrade: when you upgrade to a newer Ubuntu release, the PPAs are disabled so using this feature, the PPAs that work with the new Ubuntu version you're using are re-enabled, leaving the others disabled

it does a lot more too, like to find a repo for a program on launchpad and install it

---

### Post by varunendra on 2012-10-22
GNUway Tech,
Your sources.list file is as it should be. What are the repos that are disabled? Perhaps the older one which contained those has been entirely replaced (I didn't know it happens since I've never upgraded myself. I prefer clean installs). May be it has been backed up as "sources.list.save" file or something alike in the sources.list.d directory. You'll have to check it yourself unless someone experienced with upgrades comes to save the trouble. If you can find it (the older file), you can manually add the relevant lines to the current sources.list files with suitable corrections if needed. Any additional ppa's are now kept in the sources.list.d directory as separate files. So you should also look in there to see if the backups (.save files) of your older ppa's are there.

Also, what *DustofDust* has suggested above sounds good to me. Perhaps it automates the same thing that I suggested above (+ more as he says). Please try what he has suggested, or try to find the older files (I believe they should have been backed up in the same directory and "sources.list.d" subdirectory), then post back their contents so we can see what additional repositories you had then. If they don't exist there, then I don't know what else to suggest, sorry.

---

### Post by GNUway Tech on 2012-10-22
varunendra,

There are 2 PPAs for Screenlets that are disabled, and so is the 1 for Google Chrome. Also, there is a "sources.list.save" file. How do I use it????

DustofDust,

I install Y PPA Manager. Can I use it with the .save file, or can it look for the disabled PPAs and enable them itself????

---

### Post by varunendra on 2012-10-22
> **GNUway Tech said:**
> varunendra,

There are 2 PPAs for Screenlets that are disabled, and so is the 1 for Google Chrome. Also, there is a "sources.list.save" file. How do I use it????..
For manually using the .save file, just open it with gedit and look for lines that start with "ppa". Then just copy-paste them at the end of the current file in use, that is, sources.list. You will have to open it with root privilege to be able to edit it, which can be done with the following command:
```
gksu gedit /etc/apt/sources.list
```

However, I think that the current method of adding ppa's is to add them as separate files in the sources.list.d subdirectory (although the above method will also work). As such, look in that directory to see if the ppa's you want exist there as separate files. They would have been backed up as .save files. Just copy them without .save in their names to make them active again. Again, you'll need root access to copy them. For example, for a file named "my-ppa.list.save" :
```
cd /etc/apt/sources.list.d
sudo cp my-ppa.list.save my-ppa.list
```

However, make sure the links in the ppa are valid (not dead), and if they point to "precise",change it to "quantal".

Once that is done, do 
```
sudo apt-get update
```
to see if everything goes without errors.

That said, I can't guarantee if the previous files would be there as I have never done upgrades myself and so I'm just guessing. Try doing this yourself, should be fun and you'll learn something (probably me too :)). If stuck or confused, just post the outputs of:
```
cat /etc/apt/sources.list.save
ls /etc/apt/sources.list.d
```

---

### Post by GNUway Tech on 2012-10-23
Still no luck adding them to sources.list myself or copying the files without .save

cat /etc/apt/sources.list.save
> # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe #Added by software-properties
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main


ls /etc/apt/sources.list.d
> google-chrome.list              screenlets-ppa-precise.list~
google-chrome.list~             screenlets-ppa-precise.list.distUpgrade
google-chrome.list.distUpgrade  screenlets-ppa-precise.list.save
google-chrome.list.save         webupd8team-y-ppa-manager-quantal.list
screenlets-ppa-precise.list


---

### Post by varunendra on 2012-10-25
Sorry for not being able to respond sooner, got real busy, and may not be able to respond next 3-4 days also, although I will if got any opportunity.

Onto the problem - 
Your sources.list.save is just a backup copy of the current sources.list file, and, as I expected, the real links are in the sources.list.d directory as separate files:
> **[COLOR="Red"]google-chrome.list[/COLOR]** screenlets-ppa-precise.list~
google-chrome.list~ screenlets-ppa-precise.list.distUpgrade
google-chrome.list.distUpgrade screenlets-ppa-precise.list.save
google-chrome.list.save [COLOR="SeaGreen"]**webupd8team-y-ppa-manager-quantal.list**[/COLOR]
[COLOR="Red"]**screenlets-ppa-precise.list**[/COLOR]
The one highlighted in red should be the one for screenlets (not sure about google-chmome.list, either it is already active or contains invalid entry), just replace 'precise' with 'quantal' in its name, and make similar corrections, if required, in the link(s) it contains. The one highlighted in green should be a currently active ppa. However, I'm a bit confused with the other ones in the list. The ones with '~' in the end suggest that you may have tried to edit them in gedit.

So at this point, I can't tell you precisely which files to edit and in what way. To help me (and anyone watching this thread) determine that, please post the contents of each file or simply attach them as an archive here.

And above all, I hope you already understand that all this exercise is just an attempt to learn how to track and tweak changes to ppa's locally. Otherwise it is always easier to go to the website where the ppa was originally added from, then pick and add the current one manually using the standard "sudo add-apt-repository" (commandline), or Software-Sources (GUI) method.

Also, what *DustofDust* suggested sounds to be even easier and fully automated way of maintaining ppa's. Have you tried thatyet?

---

### Post by GNUway Tech on 2012-10-26
So far, I've tried everything you guys have suggested and none of it has worked. It looks like I'm going to have to go to the drawn out fix of clean installing.

Like I said, this happens each and every time there is an upgrade. I have no idea why Chrome and Screenlets are the only ones that have this problem.

---

### Post by deadvirus on 2013-04-27
> **GNUway Tech said:**
> So far, I've tried everything you guys have suggested and none of it has worked. It looks like I'm going to have to go to the drawn out fix of clean installing.

Like I said, this happens each and every time there is an upgrade. I have no idea why Chrome and Screenlets are the only ones that have this problem.

I also have this problem every time I upgrade Ubuntu and the only way I could have "fix" it was by manually removing/cleaning the files and re-add each repo.

---

