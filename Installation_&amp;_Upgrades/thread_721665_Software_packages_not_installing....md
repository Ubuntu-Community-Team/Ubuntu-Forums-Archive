---
title: "Software packages not installing..."
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by torbuntu on 2008-03-11
Hi,

I bought the Sobell book "a practical guide to ubuntu linux" with ubuntu 7.10 on a dvd. I installed the ubuntu using automatic install on a dual PIII system. It works now, but I wanted to add kppp because that program was not included in the automatic installation. When using the graphical add/remove of packages nothing can be added. Typing in a window

sudo apt-get install kppp

gives the answer no such package.

I think the problem has something to do with that the dvd isn't used in the install package process, even though I clicked the box that it's there. I'm clueless. Didn't Sobell include anything on his dvd, or what is the problem?

Thanks for any idea...

---

### Post by Pumalite on 2008-03-11
I suspect you just have to fix your sources.list
Post:
cat /etc/apt/sources.list

---

### Post by kellemes on 2008-03-11
Do you have an internet connection? If so.. you better use the online repositories to get your software, this way you'll be up to date.
Please post the contents of /etc/apt/sources.list

You can..
```
cat /etc/apt/sources.list
```
and copy/paste the output in your post.

---

### Post by forestpixie on 2008-03-11
well it's definitely in the repos - so I guess there's a problem with your software sources - open that it's in system > admin

tick all the boxes except source code and untick the cd rom for the moment, reload

and try the apt-get command again

and have no idea who sobell is :)

---

### Post by aysiu on 2008-03-11
If you're using *kppp* to set up your dial-up connection, and your dial-up connection is your only internet connection, then you're in a bit of a catch-22.

---

### Post by torbuntu on 2008-03-11
First, is there a way for me to track my own posts, so I don't have to search through the list of other's in order to find this again?

cat /etc/apt/sources.lst

no such file or directory

---

### Post by torbuntu on 2008-03-11
.list it was, not .lst. alright. I'll be back.

---

### Post by psp219 on 2008-03-11
if you are using dial-up, why dont you try download and put files on CD or flash drive and t hen transfer there?

---

### Post by torbuntu on 2008-03-11
I have AOL and don't know how to install penggy over Windos (or linux). I'm a beginner.


cat /etc/apt/sources.list

gave cdrom and a bunch of http:// that weren't accessable.


Clicking cdrom as a source in the repos gives the response

use apt-cdrom to make the cdrom accessible.

typing apt-cdrom add in a windows gives

/var/lib/apt/lists/ubuntu not accessible


running ubuntu live after I lost its boot file I could install packages, though some were missing, like parts of the kppp program.


I have not created a root account.

---

### Post by torbuntu on 2008-03-12
Trying to figure out if the dvd is more or less empty, I un-installed a software package which had been installed during the automatic installation, but when I wanted to re-install the same software package the response was no, like with the kppp software package.

Is there someting besides

apt-cdrom add

that I need to do?

---

### Post by Pumalite on 2008-03-12
You need to copy and paste here the output of:
cat /etc/apt/sources.list

---

### Post by torbuntu on 2008-03-12
torbuntu@torbuntu-desktop:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



# Line commented out by installer because it failed to verify:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted



## Major bug fix updates produced after the final release of the

## distribution.

# Line commented out by installer because it failed to verify:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

# Line commented out by installer because it failed to verify:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

# Line commented out by installer because it failed to verify:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

# Line commented out by installer because it failed to verify:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

# Line commented out by installer because it failed to verify:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse



## Uncomment the following two lines to add software from Canonical's

## 'partner' repository. This software is not part of Ubuntu, but is

## offered by Canonical and the respective vendors as a service to Ubuntu

## users.

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner



# Line commented out by installer because it failed to verify:

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Line commented out by installer because it failed to verify:

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Line commented out by installer because it failed to verify:

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

# Line commented out by installer because it failed to verify:

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

# Line commented out by installer because it failed to verify:

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

# Line commented out by installer because it failed to verify:

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted

torbuntu@torbuntu-desktop:~$

---

### Post by Pumalite on 2008-03-12
Backup your file first:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Now:
gksudo gedit /etc/apt/sources.list
Uncomment (remove # from the front of) all lines that start with 'deb', do not uncomment lines with 'deb-src'
Save, exit, 
Now:
sudo aptitude update
sudo aptitude upgrade

---

### Post by torbuntu on 2008-03-12
Did the stuff and it still doesn't work. The first print out is from the repos after clicking what sources of code I have, the next is from /etc/apt/sources.list


ttp://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'

[http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:) Could not resolve 'archive.canonical.com'

[http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2:) Could not resolve 'archive.canonical.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'security.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:) Could not resolve 'archive.canonical.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) Could not resolve 'security.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'

[http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:) Could not resolve 'archive.canonical.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:) Could not resolve 'security.ubuntu.com'

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:) Could not resolve 'security.ubuntu.com'

cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs



^[[Atorbuntu@torbuntu-desktop:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted



## Major bug fix updates produced after the final release of the

## distribution.

# Line commented out by installer because it failed to verify:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe #Added by software-properties

# Line commented out by installer because it failed to verify:



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe #Added by software-properties



## Uncomment the following two lines to add software from Canonical's

## 'partner' repository. This software is not part of Ubuntu, but is

## offered by Canonical and the respective vendors as a service to Ubuntu

## users.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner



# Line commented out by installer because it failed to verify:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe #Added by software-properties

# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

# Line commented out by installer because it failed to verify:

# Line commented out by installer because it failed to verify:

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted universe main multiverse

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted

torbuntu@torbuntu-desktop:~$

---

### Post by torbuntu on 2008-03-12
P.S. I used the apt-cdrom add command. No success.

---

### Post by Pumalite on 2008-03-12
Try changing your Server

---

### Post by torbuntu on 2008-03-12
No results. DVD is not used in the software package add/remove process. Too bad. ubuntu seems nice otherwise, but useless as is.

---

### Post by torbuntu on 2008-03-13
Thanks anyway. I appreciate that you tried. You know more about this than me.

---

