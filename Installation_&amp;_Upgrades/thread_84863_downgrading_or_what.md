---
title: "downgrading or what??"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by maltje on 2005-11-01
yesterday i had changed my sources.list,try to get something to work.
But it didn't work.
I forgot to put my sources.list back as before.
This morning I got message that there where a lot of updates,so I let him do that.
But now I see that my ubuntu is in English (with a little dutch)!!!!!!and not in dutch like before!!!!
How can I get him back in Dutch ???
I tried sudo base-config and marked Belgium but it is still the same.
here is my sources.list after the change

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse


## Security updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

## Extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Officials Backports
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

## Backports
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

## KDE 3.4.2
## deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

## PHP5
## deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 hoary

## suPHP (src)
## deb-src [http://manu.home-dn.net/debian/suphp-preview](http://manu.home-dn.net/debian/suphp-preview) sid main

## Wine
## deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) hoary
## Breezy Badger (5.10)

deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe

## Backports
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted


I changed it back to 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main ##universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe ##multiverse restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

but everything is still the same

---

### Post by Kyral on 2005-11-01
Replace "us" with the Dutch country code (de?) and try updating again

---

### Post by Chris Chan on 2005-11-01
[QUOTE=Kyral]Replace "us" with the Dutch country code (de?) and try updating again[/QUOTE]
The Dutch country code is 'nl'. 'de' is Germany.

---

### Post by duffmckagan on 2005-11-02
Hehe.....are you confused with Deutsch (German) with Dutch!   ;-)

---

### Post by maltje on 2005-11-02
For Belgium it's be and "be" are in the text.

---

