---
title: "dist-upgrade removed shotwell"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by rabicula on 2013-03-20
a dist-upgrade this morning removed shotwell

```
sudo apt-get dist-upgrade
[sudo] password for halim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libgexiv2-0 shotwell
The following packages will be upgraded:
  libgexiv2-1 libperl-dev libperl5.14 perl perl-base perl-modules
6 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 12.3 MB of archives.

```

And I can't get it back:

```
apt-get install shotwell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 shotwell : Depends: libgstreamer-plugins-base1.0-0 (>= 1.0.0) but it is not installable
            Depends: libgstreamer1.0-0 (>= 1.0.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by schragge on 2013-03-20
Judging from the libgstreamer version it tries to install, you're running *raring*, right? Or are you trying to install the latest shotwell from the [Yorba PPA]("https://launchpad.net/%7Eyorba/+archive/ppa") on an older Ubuntu release?

---

### Post by rabicula on 2013-03-20
Hello,
I am not using raring, it is a regular precise LTS,
Please find bellow the distrib and kernel versions:
```
~ # cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"
~ # uname -r
3.2.0-36-generic

```

I did try to use the yorba ppa but that was after the dist-upgrade did remove shotwell. yorba PPA gave me the exact same results :(

---

### Post by schragge on 2013-03-20
Disable the Yorba PPA in your software sources, then try to install shotwell again (shotwell from the *precise* repository shouldn't depend on libgstreamer1.0 as it depends on libgstreamer0.10):
```

sudo apt-get update
sudo apt-get install shotwell

```

[highlight]NB.[/highlight] This probably has nothing to do with your problem, but you might want to upgrade to a newer kernel as described at [uwiki]Kernel/LTSEnablementStack[/uwiki].

---

### Post by eric-yorba on 2013-03-20
FYI, if you're going to install Shotwell from our PPA, you also have to add **ppa:gstreamer-developers/ppa**

---

### Post by andan on 2013-03-20
Got the exactly same issue today, since I'm not interested in adding PPA, it is there a workaround to have Shotwell installable from USC? Spent quite a lot time to organize my whole photo collection for Shotwell and I dont wanna search for new photo organizer.

---

### Post by eric-yorba on 2013-03-20
> **andan said:**
> Got the exactly same issue today, since I'm not interested in adding PPA, it is there a workaround to have Shotwell installable from USC? Spent quite a lot time to organize my whole photo collection for Shotwell and I dont wanna search for new photo organizer.

How did you run into this issue without adding a PPA?

---

### Post by tgalati4 on 2013-03-20
What was the reason that you used *dist-upgrade* instead of *upgrade* with apt-get?

---

### Post by cometdog on 2013-03-20
> **eric-yorba said:**
> FYI, if you're going to install Shotwell from our PPA, you also have to add **ppa:gstreamer-developers/ppa**

Thank you!  This solved my problem when trying to install 0.14 from the ppa:yorba/ppa repository today on Precise.

This should probably be noted somewhere on the Ubuntu installation instructions here
[http://yorba.org/shotwell/install.html](http://yorba.org/shotwell/install.html)

---

### Post by eric-yorba on 2013-03-20
> **cometdog said:**
> Thank you!  This solved my problem when trying to install 0.14 from the ppa:yorba/ppa repository today on Precise.

This should probably be noted somewhere on the Ubuntu installation instructions here
[http://yorba.org/shotwell/install.html](http://yorba.org/shotwell/install.html)

Good catch!

I think we'll just copy the required GStreamer 1.0 packages into our own PPA and save Precise users a step.

---

### Post by andan on 2013-03-22
> **eric-yorba said:**
> How did you run into this issue without adding a PPA?

Regular apt-get update and upgrade command resulted in deleting Shotwell, when trying to re install using USC, it didin't work, however it worked today after last regular ubuntu update and I have Shotwell 0.14.0 installed.

---

### Post by linfidel on 2013-03-27
I recently lost Shotwell in 12.04 too, doing the regular update when prompted by the update manager.  I do remember seeing that it was going to remove shotwell, but I didn't really think about it too much at the time, and didn't really know why.

But I had no problem reinstalling it today (0.14.0) and it remembers my folders and tags.  But it's a bit rude of the installer to remove it like that.

---

