---
title: "Re enabling Ppa's"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-02-02
How can i re enable all my ppa's that worked in karmic to work in lucid, since they were disabled on the upgrade?

---

### Post by ronacc on 2010-02-02
if they are still in your /etc/apt/sources.list  , just change karmic to lucid and uncomment them . otherwise you will have to add them back one at a time .

---

### Post by sports fan Matt on 2010-02-02
E: Type 'Uncomment' is not known on line 37 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Can anyone help?

---

### Post by sports fan Matt on 2010-02-02
I think I fixed it..can ya'll take a look?

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main  disabled on upgrade to lucid
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe

---

### Post by VMC on 2010-02-02
I wouldn't know what to look for, since I don't use PPA's, or rarely use them.

What happens when you do an update? Any ignores or errors.
Or are you asking should you include more PPA's?

---

### Post by nanotube on 2010-02-03
looks like the only repository in your list that's not part of the 'official ubuntu repositories' is the ubuntuzilla repo. 

that one doesn't need to be changed for different versions of ubuntu... just keep it as is (but remove the 'disabled ...' text at the end which you put there)

---

### Post by zika on 2010-02-03
Looks like You do not have ppa's in Your source.list, except ubuntuzilla... That is OK.
In Lucid, now, You have a folder **/etc/apt/sources.list.d** where ppa's are stored...> ~$ ls /etc/apt/sources.list.d
chromium-daily-ppa-lucid.list          thefirstm-lucid-lucid.list
chromium-daily-ppa-lucid.list.save     thefirstm-lucid-lucid.list.save
medibuntu.list                         ubuntu-mozilla-daily-ppa-lucid.list
medibuntu.list.save                    ubuntu-mozilla-daily-ppa-lucid.list.save
network-manager-trunk-lucid.list       xorg-edgers-ppa-lucid.list
network-manager-trunk-lucid.list.save  xorg-edgers-ppa-lucid.list.save
opera.list.saveYou'll notice .save files that are for re-enabling ppa, once it was disabled...

---

### Post by sports fan Matt on 2010-02-03
Apologizes to all as I'm just getting around to this.  Here is the output from the ubuntuzilla script:  Failed to fetch [http://downloads.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz](http://downloads.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I am confused about nano and zika's instructions though..Can anyone help?  (part im cinfused on is how to access the /etc/apt/sources.list.d and what to uncomment.  I think I can use Sudo gedit  /etc/apt/sources.list.d and see the folder...

---

### Post by nanotube on 2010-02-03
> **sox fan Matt said:**
> Apologizes to all as I'm just getting around to this.  Here is the output from the ubuntuzilla script:  Failed to fetch [http://downloads.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz](http://downloads.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

it seems you have copied a forum-truncated sources.list line for ubuntuzilla (note the ... in the middle).

the correct sources.list line for ubuntuzilla is:
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```


about the sources.list.d directory - it's just a directory... you can just list the contents to see if you have anything there, using the following command:
```
ls -al /etc/apt/sources.list.d/
```

---

### Post by zika on 2010-02-03
> **sox fan Matt said:**
> Apologizes to all as I'm just getting around to this.  Here is the output from the ubuntuzilla script:  Failed to fetch [http://downloads.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz](http://downloads.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I am confused about nano and zika's instructions though..Can anyone help?  (part im cinfused on is how to access the /etc/apt/sources.list.d and what to uncomment.  I think I can use Sudo gedit  /etc/apt/sources.list.d and see the folder...Do not use sudo with gedit. Sudo goes with nano and CLI apps and gksu goes with gedit and GUI apps. I did not give any instructions. Simply replace karmic with lucid in every *.list file in /etc/apt/sources.list.d provided that that ppa have packages for Lucid. You might do the same with *.save files to be safe. Or, alternatively, You could re-introduce all the ppa's You really need through Software sources option in System>Administration...

---

