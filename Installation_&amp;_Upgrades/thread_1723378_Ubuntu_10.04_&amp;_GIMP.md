---
title: "Ubuntu 10.04 &amp; GIMP"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by JohnHeikkila on 2011-04-07
So I just got a fresh install of Ubuntu, and I was kinda sad to know there was no GIMP in the repos. (Or then it's my sources.list's fault)
This is why I googled it a bit and found this "tutorial"
[http://www.howtogeek.com/howto/12047/install-gimp-2.7.1-on-lucid-lynx-using-ppa/](http://www.howtogeek.com/howto/12047/install-gimp-2.7.1-on-lucid-lynx-using-ppa/)

After following that, all the way to installing GIMP, I got this output from the console:
```
tikku@Tikku:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgegl-0.0-0 (>= 0.1.3-2010072601~ll) but it is not going to be installed
        Depends: libmng1 (>= 1.0.3-1) but it is not installable
E: Broken packages
```And after using Firefox, going to youtube results in "Installing Missing plugin" which results in "Could not find package flashplugin-installer"

I find this very odd, because I've been able to install that one when booted onto the Live-CD.

Sources.list:
```
deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties

deb http://fi.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

deb http://fi.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

deb http://fi.archive.ubuntu.com/ubuntu/ lucid universe
deb http://fi.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://fi.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://fi.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
```

Ohh, and same thing with another program, after trying to manually install flashplugin-installer:
```
tikku@Tikku:~$ apt-file --package-only search nspluginwrapper
The program 'apt-file' is currently not installed.  You can install it by typing:
sudo apt-get install apt-file
tikku@Tikku:~$ sudo apt-get install apt-file
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apt-file
```

---

### Post by zvacet on 2011-04-07
```
gksudo gedit /etc/apt/sources.list
```

Leave first line ( about CD ) and replace rest of your source list with this

> deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

If you still get problems under ubuntu software center >edit > software repositories> change to main.

---

