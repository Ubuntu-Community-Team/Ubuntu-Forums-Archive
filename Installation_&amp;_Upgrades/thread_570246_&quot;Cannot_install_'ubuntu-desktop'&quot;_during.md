---
title: "&quot;Cannot install 'ubuntu-desktop'&quot; during 7.04-7.10 upgrade"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by jmusso on 2007-10-08
As the title implies, when I try to upgrade to 7.10, I get an error message that says it can't install 'ubuntu-desktop'. I'm running Beryl on my current 7.04, so I'm wondering if all the tinkering with that has ran me into some trouble... Also should I try disabling my restricted ATI drivers? Anything would help. The update to 7.10 won't continue because of this. Thanks!

---

### Post by forestpixie on 2007-10-08
don't know if this will help - I think you have to have ubuntu-desktop installed before you can upgrade to 7.10. Did you remove anything that was part of the ubuntu-desktop meta package?

I had to revert to the Ubuntu openoffice before I could, try installing that first

```
sudo apt-get install ubuntu-desktop
```

if it says it's going to install something that could be the problem

---

### Post by jmusso on 2007-10-08
```
joe@joe:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: ubuntu-sounds but it is not going to be installed
E: Broken packages
joe@joe:~$ 

```

...?

---

### Post by rsambuca on 2007-10-08
Two questions.  What method of upgrading are you trying, and can you post your sources.list?

---

### Post by jmusso on 2007-10-08
the method I'm trying is sudo update-manager -d (If that's not exactly the right method, I'm just forgetting it for the moment - I've been using the one recommended on ubuntu.com, and I know when I tried it I typed it correctly.) 

Secondly, i'm not exactly sure how to pull up my sources.list , but I did a sudo gedit sources.list and it was a blank document.

---

### Post by rsambuca on 2007-10-08
try 

cat /etc/apt/sources.list

---

### Post by jmusso on 2007-10-08
```
joe@joe:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://archive.ubuntustudio.org/ubuntustudio feisty main

deb http://ubuntu.beryl-project.org/ feisty main

 ## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
joe@joe:~$ 

```

thanks. Here you go.

---

### Post by rsambuca on 2007-10-08
You have some non-standard repositories which might make upgrading a little problematic.  Having said that, the ubuntu-desktop issue I think is unrelated to that.

You can try 

sudo aptitude install ubuntu-desktop

---

### Post by forestpixie on 2007-10-08
> You can try

sudo aptitude install ubuntu-desktop

d'oh - that's what I meant to say :)

re - the repo's - when I upgraded last week - the upgrade told me I had non-standard repo's and then disabled them, then it carried on

---

