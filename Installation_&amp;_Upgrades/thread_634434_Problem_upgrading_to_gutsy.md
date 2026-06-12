---
title: "Problem upgrading to gutsy"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Spacedementia87 on 2007-12-07
Just tried the upgrade tool and I get this error message:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found


I am assuming that the upgrade tool retains all the extra packages that I have installed on my feisty distro?

---

### Post by linuxwizard on 2007-12-07
Remove or disable all extra repos you added to your source list. Than try upgrading again.

---

### Post by Spacedementia87 on 2007-12-07
I have disabled all the ones that look non-official.  Still won't work

---

### Post by taurus on 2007-12-07
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Spacedementia87 on 2007-12-07
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt feisty main

# deb http://archive.canonical.com/ubuntu feisty-commercial main

# deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

# deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

#AUTOMATIX REPOS END
# deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main

```

---

### Post by taurus on 2007-12-07
You need to edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of all the lines below.

```

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
#deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
#deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main

```

Save it and run

```
sudo apt-get update
```
Now, see if you can upgrade to Gutsy now.

---

### Post by Spacedementia87 on 2007-12-08
ok thank you, that seemed to work.

So I left it on updating over night this morning I wondered whether it had updated because it all looked exactly the same so I restarted and after the splash screen I just get a black screen and nothing happens.

How do I fix this?

---

### Post by Spacedementia87 on 2007-12-08
bump

---

### Post by taurus on 2007-12-08
See if you can reconfigure your X server again.  Press <Ctrl><Alt>F2 to get to a console.  Log in with your username and password.  Then, at the prompt, run

```
sudo dpkg-reconfigure xserver-xorg
```
When you are done with it, get back to GUI login screen with <Alt>F7 and restart X server again with <Ctrl><Alt>Backspace.

p.s.  For now, I would recommend you pick **vesa** driver for your graphic card until you get X up and running again.  Then, install the right driver for your graphic card.

---

### Post by Spacedementia87 on 2007-12-08
ok i'll give that a go.  Thanks

---

### Post by Spacedementia87 on 2007-12-08
ok after a few goes that seemed to work.  Now I have got in with a minimal screen resolution and no fanciness.

I enabled my restricted driver and rebooted and still cannot put the resolution above 800x600.  Tried running my nvidia config tool and it said to run "nvidia-xconfig" in the terminal so I did and restared still the same, asking me to run that again if i try and open the nvidia program.

How do I get my high res back?

---

### Post by daedalusman on 2007-12-20
I'm having the same problem that was stated in the first post, 404 on mediubuntu servers. Here is my sources.list contents...  
 ```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

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
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe #Added by software-properties

## gift
#deb http://apt.cerkinfo.be/ unstable main contrib
#deb-src http://apt.cerkinfo.be/ unstable main contrib 

##moblock
#deb http://moblock-deb.sourceforge.net/debian unstable main
#deb-src http://moblock-deb.sourceforge.net/debian unstable main

```

Can anyone help me with this problem? Thanks.

---

### Post by rsambuca on 2007-12-20
I don't think you can be having that same error since I don't see the medibuntu repositories in your sources list.  Can you post the exact error message that is output?

---

