---
title: "Unable to upgrade to 10.04"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by squeak24 on 2010-08-25
I have been trying to upgrade to 10.04, I have tried a few times, I have had various issues like not enough space which I cleared up.

Just tried it again, after nearly two hours it came up with this error

Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc-data_1.0.6-1ubuntu1.1_all.deb](http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc-data_1.0.6-1ubuntu1.1_all.deb) 404  Not Found [IP: 194.117.143.71 80]
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1.1_i386.deb](http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1.1_i386.deb) 404  Not Found [IP: 194.117.143.71 80]
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1.1_i386.deb](http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1.1_i386.deb) 404  Not Found [IP: 194.117.143.71 80]
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc-nox_1.0.6-1ubuntu1.1_i386.deb](http://ubuntu.virginmedia.com/archive/pool/universe/v/vlc/vlc-nox_1.0.6-1ubuntu1.1_i386.deb) 404  Not Found [IP: 194.117.143.71 80]

Do any of the other distributions work?

---

### Post by dtoronto on 2010-08-25
What distro are you upgrading from?  I would highly recommend doing a reinstall when upgrading distro releases.

---

### Post by lechien73 on 2010-08-25
It would be good to know what distro you're upgrading from, as **dtoronto** said.

Also, if you could post the contents of your /etc/apt.d/sources.list file, this will help us to see where your distribution is looking for its packages.

---

### Post by mörgæs on 2010-08-25
First of all, are you sure that 10.04 works well on this machine? Have you tried a live boot?

---

### Post by squeak24 on 2010-08-25
Thanks for your speedy responses

I am using Ubuntu 9.10 - the Karmic Koala at the moment. I mainly use Ubuntu, I do have Vista installed on another partition, I try avoid using that at all costs.

Here is my /etc/apt.d/sources.list file contents.

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.virginmedia.com/archive/ karmic main restricted
deb-src http://ubuntu.virginmedia.com/archive/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.virginmedia.com/archive/ karmic-updates main restricted
deb-src http://ubuntu.virginmedia.com/archive/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.virginmedia.com/archive/ karmic universe
deb-src http://ubuntu.virginmedia.com/archive/ karmic universe
deb http://ubuntu.virginmedia.com/archive/ karmic-updates universe
deb-src http://ubuntu.virginmedia.com/archive/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.virginmedia.com/archive/ karmic multiverse
deb-src http://ubuntu.virginmedia.com/archive/ karmic multiverse
deb http://ubuntu.virginmedia.com/archive/ karmic-updates multiverse
deb-src http://ubuntu.virginmedia.com/archive/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ubuntu.virginmedia.com/archive/ karmic-security main restricted
deb-src http://ubuntu.virginmedia.com/archive/ karmic-security main restricted
deb http://ubuntu.virginmedia.com/archive/ karmic-security universe
deb-src http://ubuntu.virginmedia.com/archive/ karmic-security universe
deb http://ubuntu.virginmedia.com/archive/ karmic-security multiverse
deb-src http://ubuntu.virginmedia.com/archive/ karmic-security multiverse

# The Campware package repository

# deb http://code.campware.org/ubuntu dapper main # disabled on upgrade to karmic
# deb http://ppa.launchpad.net/sunab/ppa/ubuntu karmic main # disabled on upgrade to karmic
# deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu karmic main # disabled on upgrade to karmic
# deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu karmic main # disabled on upgrade to karmic
deb http://www.radio.warwick.ac.uk/debian-raw/ lenny main


```

It is doing all the initial checks, just won't download the full package. I haven't tried a live boot. Do you think it would be better to download the CD image, and upgrade that way. I have been trying it via the Internet so far.

Again, many thanks for your assistance, it is greatly appreciated.

---

### Post by mörgæs on 2010-08-25
Whoa, this poor thing has been upgraded at least from 8.10. I think it deserves a clean install.

Remember to have wired internet access while installing.

---

### Post by lechien73 on 2010-08-25
Since you're not using the standard repositories, you may be missing updates, so a re-install would be the best bet. Do a full backup first, and especially make sure you've backed up your /home folder, so you don't lose any documents.

Also, as a previous poster mentioned, make sure you're happy that 10.04 works with your hardware by testing the Live CD first.

I do think a complete re-install is best, but if you absolutely want to try the upgrade route, then you change each reference to [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) to [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) in your /etc/apt/sources.list file. Type:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.backup
gksu gedit /etc/apt/sources.list
```

to make a backup and then edit it. After modifying and saving it, type:

```
sudo apt-get update
```

to update the sources. You may have a lot of updates to install, but you should then be able to upgrade your distribution. I'll repeat that I think a complete re-install would be best, and I'm not sure how well an upgrade would work with your system. I just want to give you both options, so it's up to you to decide :)

---

### Post by techxcell on 2010-08-25
Agreeing with @liechen73 I will just like to reduce your work a bit more.

Start with the a new /etc/apt/sources.list and add just one line in it:

```
deb http://archive.ubuntu.com/ubuntu karmic main restricted  multiverse universe
```Save the file and issue the command

```
sudo apt-get update
```If no errors are reported, all is well.. so issue

```
 sudo apt-get dist-upgrade
```

---

### Post by squeak24 on 2010-08-25
thanks for all your advice, it is really appreciated. 

I will take a look tomorrow. I normally save all my data to an external HD, will be going through the applications tomorrow to see what I actually use, and run the live test CD to see if it works.

---

