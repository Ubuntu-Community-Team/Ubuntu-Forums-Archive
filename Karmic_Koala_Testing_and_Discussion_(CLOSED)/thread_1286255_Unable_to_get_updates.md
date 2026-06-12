---
title: "Unable to get updates"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cjnkns on 2009-10-08
Does anyone else have an issue getting updates tonight?

My update stalls when trying to get the linux image file.

---

### Post by emarkay on 2009-10-08
Was good an hour ago - reboot and try again.  :)

---

### Post by ranch hand on 2009-10-08
I up dated systems before and after you posted just fine.

It might be a good idea to run;
```

sudo dpkg --configure -a

```
to make sure you don't have anything stuck in the system.

---

### Post by NRDNick on 2009-10-09
Sorry to hijack the thread but it seems maybe the op has sorted out their issue, and I didn't feel it necessary to start a new thread. 

My question is this, when did you last receive updates to Karmic? If I check my synaptic logs the last updates to packages I received was on Oct 4. This seemed odd to me, as I had assumed even still in the beta we would receive regular updates until the we hit the release candidate. 

I have tried the suggested " sudo dpkg --configure -a " and still there are no updates available. I have read about people having problems with the new 2.6.31-12 Kernel yet the newest I can see in my repos is the 2.6.31-11 Kernel. Am I missing something here? Are you guys using a PPA to get that Kernel? Any help would be appreciated.

---

### Post by cjnkns on 2009-10-09
> Sorry to hijack the thread but it seems maybe the op has sorted out their issue, and I didn't feel it necessary to start a new thread.


No - I rebooted and that got me gonig again. Not sure why things were stalling but the reboot helped. Thanks!

---

### Post by ranch hand on 2009-10-09
Have rebooted your box since that last update of yours?

We are actually getting 31-13 after a couple or 3 32-12s.  You have quite a backlog.

After you ran the dpkg stuff did you run "sudo apt-get update"?

Just hoping maybe it is a synaptic problem only, there has been an update on it.

---

### Post by NRDNick on 2009-10-09
I have rebooted several times, I'm actually using the 31-10 Kernel right now as I found I was getting better opengl performance from it over 31-11.

I did run "sudo apt-get update" after running the dpkg stuff yes, so it's not simply a synaptic problem. 

Any other ideas?

---

### Post by kansasnoob on 2009-10-09
> **NRDNick said:**
> Sorry to hijack the thread but it seems maybe the op has sorted out their issue, and I didn't feel it necessary to start a new thread. 

My question is this, when did you last receive updates to Karmic? If I check my synaptic logs the last updates to packages I received was on Oct 4. This seemed odd to me, as I had assumed even still in the beta we would receive regular updates until the we hit the release candidate. 

I have tried the suggested " sudo dpkg --configure -a " and still there are no updates available. I have read about people having problems with the new 2.6.31-12 Kernel yet the newest I can see in my repos is the 2.6.31-11 Kernel. Am I missing something here? Are you guys using a PPA to get that Kernel? Any help would be appreciated.

You might want to post your sources.list, that is the output of:

```
cat /etc/apt/sources.list
```

There have been many, many updates.

You might just need to run:

```
sudo apt-get update && sudo apt-get upgrade
```

Update manger has experienced some problems throughout the development cycle, which is normal.

---

### Post by NRDNick on 2009-10-09
Here is my sources list, I added the mediabuntu repos following a multimedia guide

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha i386 (20090902.1)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic universe
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic universe
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates universe
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic multiverse
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic multiverse
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates multiverse
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse          <------ not sure why these are commented out, I didn't do it
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security main restricted
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security universe
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security universe
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security multiverse
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security multiverse
# deb [http://ppa.launchpad.net/ari-tczew/ppa/ubuntu](http://ppa.launchpad.net/ari-tczew/ppa/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/ari-tczew/ppa/ubuntu](http://ppa.launchpad.net/ari-tczew/ppa/ubuntu) karmic main
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-backports restricted main multiverse universe
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-proposed restricted main multiverse universe

I tried running sudo apt-get update && sudo apt-get upgrade 

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks for the help guys:P

---

### Post by slakkie on 2009-10-09
Try a different mirror, could be that it is a bit out of sync:

```

The following packages will be upgraded:
  devicekit-disks [007-1ubuntu1 -> 007-2]  hpijs [3.9.8-1ubuntu1 -> 3.9.8-1ubuntu2]
  hpijs-ppds [3.9.8-1ubuntu1 -> 3.9.8-1ubuntu2]  hplip [3.9.8-1ubuntu1 -> 3.9.8-1ubuntu2]
  hplip-data [3.9.8-1ubuntu1 -> 3.9.8-1ubuntu2]  libgl1-mesa-dri [7.6.0-1ubuntu1 -> 7.6.0-1ubuntu2]
  libgl1-mesa-glx [7.6.0-1ubuntu1 -> 7.6.0-1ubuntu2]  libglu1-mesa [7.6.0-1ubuntu1 -> 7.6.0-1ubuntu2]
  mesa-utils [7.6.0-1ubuntu1 -> 7.6.0-1ubuntu2]  mountall [0.1.8 -> 0.2.0]  pidgin-otr [3.2.0-4 -> 3.2.0-4ubuntu1]
  plasma-widget-indicatordisplay [0.4.1-0ubuntu2 -> 0.4.2-0ubuntu1]  update-notifier [0.88 -> 0.89]
  update-notifier-common [0.88 -> 0.89]  xserver-common [2:1.6.3-1ubuntu7 -> 2:1.6.4-2ubuntu1]
  xserver-xorg-core [2:1.6.3-1ubuntu7 -> 2:1.6.4-2ubuntu1]
16 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by NRDNick on 2009-10-09
> **slakkie said:**
> Try a different mirror, could be that it is a bit out of sync:

Oh wow was it ever! There they are! lol Thanks for the help guys, and wish me luck! :P

---

### Post by ranch hand on 2009-10-09
Good luck.

LET THE FUN BEGIN

---

