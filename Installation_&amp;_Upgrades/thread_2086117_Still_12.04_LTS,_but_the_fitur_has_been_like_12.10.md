---
title: "Still 12.04 LTS, but the fitur has been like 12.10"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by lemonadejuice on 2012-11-19
Well, actually it's a bit long story how my ubuntu 12.04 could come like this.

I want to upgrade to 12.10, at first it going well but my internet connection going down suddenly and i need to cancel the upgrade (it still downloading the package at the time). After some hours i want to do the upgrade again but the update-manager don't detect any new version, when i did update, i realized that my source has been change to quantal sources. 

SInce it had been long time since i do last upgrade, i do the upgrade.

but once again when the terminal ask for flashplugin-installer, but cause some condition i need to cancel it.

When i switch on my computer again, the upgrade continue and finished like it should done . I restart the computer but when i go to the desktop, it's just blank screen, i think that i should just do the upgrade to 12.10 to fix it, i go to update manager from terminal but the new release is 13.04 alpha version, i still do the upgrade but when in the middle proceed of get new sources channel it just closed. 

I found that my unity is missing, so i install the unity. But now my sources has change to 13.04 sources (raring), now the unity going smoothly, and i restart again.

All my desktop back to normal but some of my program gone (like wine), my graphic and another thing that should only able above 12.10 version  are installed on my 12.04 LTS. I want to upgrade to 12.10 now, but the update-manager tell me that the new release is 13.04. I can't install the wine, it told me that it only available from multiverse sources.

what should i do now? i really need the wine

---

### Post by BertN45 on 2012-11-19
In one way or another you succeeded in getting the development version 13.04 installed. There is only one way back to 12.10 (or 12.04) and that is a clean install from scratch. But first save all what you want to keep on another disk/usb stick or dvd.

If you want, you could try to back-up your Home place or folder too, but first make all hidden files visible (CTRL+h). If you restore the home back-up you have probably most of your settings back and also everything in Documents, Pictures etc. Keep the same username in the new installation to avoid problems with file permissions.

---

### Post by lemonadejuice on 2012-11-19
If i upgrade to 13.04 will it possible to me to install wine? Well, there's so much important program and it'll be waste to install again all of it.

---

### Post by deadflowr on 2012-11-19
Wow, this seems pretty interesting.

Please post the following outputs:

```
lsb_release -a
```

```
cat /etc/apt/sources.list
```

I only ask for these to verify that you're running raring.

I really have no idea what you did to upgrade to raring.
It is important to note that you should never cancel an update midway through as this is the best way to bork up the system.

As an added note, LTS releases, such as 12.04 by default are set to upgrade to LTS-releases. To change that, you need to go to the software sources(this can be accessed through the settings in the update manager) click on the updates tab in software sources and change the notify of new versions to something other than lts releases. close it(do not revert) and click the check box in the update manager.

Unfortunately I don't use wine, or at least haven't had to install it on development releases, but I believe an uninterrupted upgrade should install it fine. However, since you cancelled the upgrade midway, all those chips are in the air.

At this point though, I would say a reinstall might be your best option.If this is the case then it is important to try to backup as much of your files as possible.

---

### Post by lemonadejuice on 2012-11-20
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
```

I realized that my system now is 12.10, i had check to details on system setting, it show me that my system is 12.10. But when log in, 12.04 LTS is what written on the bottom corner of desktop. 

```



# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ precise main restricted

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ raring-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-security universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main

deb http://archive.ubuntu.com/ubuntu quantal multiverse universe
deb-src http://archive.ubuntu.com/ubuntu quantal multiverse universe #Added by software-properties

```

---

### Post by lemonadejuice on 2012-11-21
Now i can install wine

i dunno if this is happen to others (if it is a bug of 12.10) when i connect to internet, after a while the ubuntu 12.10 will become very slow, lagging and hang. I'm sure it's not about specs cause when i'm not connect to internet the ubuntu run smoothly as long as i used. 

Before it happen i got someproblem with nm-applet, nm-applet won't launched automatically but still launched when i give command nm-applet on terminal. 

I think is unity problem again, i run unity --reset, but unity told me reset option had changed to deprecated. I run it and my nm-applet back (at that time i'm not connect to internet) and my ubuntu just running normal.

This afternoon, when i connect to my shcool wireless the lagging come back

Is the network manager is the main problem?

---

### Post by BertN45 on 2012-11-21
You main problem is that you have a source list that is completely mixed up. It has most entries pointing to 13.04, the raring entries and some to 12.10 the quantal entries.

Your operating system is partly 12.10 and mostly 13.04 now and as you explained there seems to be some left-overs from 12.04.

It is a miracle that your system is still working more or less. Save what you want to keep as fast as possible and do a clean re-install. This strange mixture of systems will deteriorate fast as more and more software will be changed as result of the raring on-going development.

Most of the software is from 13.04 raring and that system will get more unstable if more new developments are going in for testing. That system is for developers and testers only and will be ready and released end of April 2013.

---

