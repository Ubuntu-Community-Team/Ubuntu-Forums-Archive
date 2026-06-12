---
title: "apt-get errors"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by ranger79 on 2005-06-09
Greetings!

I'm trying to install the codecs following the ubuntu guide.

I've got the following errors:
============================================
hk@hk:~$ sudo apt-get install gstreamer0.8-plugins
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-plugins: Depends: gstreamer0.8-a52dec but it is not going to be installed
                        Depends: gstreamer0.8-aa but it is not installable
                        Depends: gstreamer0.8-artsd but it is not installable
                        Depends: gstreamer0.8-caca but it is not installable
                        Depends: gstreamer0.8-festival but it is not installable
                        Depends: gstreamer0.8-jack but it is not installable
                        Depends: gstreamer0.8-mad but it is not going to be installed
                        Depends: gstreamer0.8-mikmod but it is not installable
                        Depends: gstreamer0.8-mpeg2dec but it is not going to be installed
                        Depends: gstreamer0.8-sid but it is not installable
                        Depends: gstreamer0.8-swfdec but it is not going to be installed
E: Broken packages
============================================

Below is my sources.lst:
============================================
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
============================================

From what I read here, the common root of the problem is usually the repositories. I've checked the list a few times to make sure that it's the same as the guide. I'm still getting the error however.

Appreciate if some one can enlighten me on what could be wrong.

Thanks.

ranger79

---

### Post by defkewl on 2005-06-09
Try installing those broken packages manually and let see what happens. Probably they don't have those packages at the repository.

---

### Post by dataw0lf on 2005-06-09
1) comment out the deb cdrom line.
2) UNCOMMENT the main restricted line right after it
3) ADD multiverse
Your new sources.list should look something like this:
```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
  deb http://sg.archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://sg.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
  deb http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://sg.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://sg.archive.ubuntu.com/ubuntu hoary universe
deb-src http://sg.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://sg.archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

4) Run apt-get update
5) Install wanted packages
6) A apt-get upgrade would probably be warranted too.

---

### Post by ranger79 on 2005-06-09
Modifying the repository list works like a champ !!

Thanks.

---

