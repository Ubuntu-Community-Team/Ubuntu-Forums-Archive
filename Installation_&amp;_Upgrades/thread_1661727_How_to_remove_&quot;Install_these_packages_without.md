---
title: "How to remove &quot;Install these packages without verification&quot;"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by vigs on 2011-01-07
[FONT=Courier New][FONT=Verdana]Whenever I do an apt-get upgrade, I get this warning:
[/FONT][/FONT][FONT=Courier New]Install these packages without verification [y/N]? 

[FONT=Verdana]How to remove this warning? Nothing in the forum has seemed to work so far for me.[/FONT]
[/FONT][FONT=Courier New]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor apparmor-utils cups cups-bsd cups-client cups-common cups-ppdc dpkg dpkg-dev ifupdown libapparmor-perl libapparmor1 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdpkg-perl libvlc5 libvlccore4 linux-generic linux-headers-generic linux-image-generic
  linux-source mozilla-plugin-vlc python-django ttf-symbol-replacement vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse wine1.2
34 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.8MB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dpkg ttf-symbol-replacement wine1.2 ifupdown libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 cups-common cups-bsd cups-client
  cups-ppdc cups dpkg-dev libdpkg-perl libvlccore4 vlc-data libvlc5 linux-generic linux-image-generic linux-headers-generic linux-source vlc-plugin-notify
  vlc-plugin-pulse vlc mozilla-plugin-vlc vlc-nox python-django apparmor libapparmor1 libapparmor-perl apparmor-utils
Install these packages without verification [y/N]? 
[/FONT]

---

### Post by 1991sudarshan on 2011-01-07
Could you pls give more details regarding this issue do you want those packages show in the show in the attachment to removed or not to be upgraded?

---

### Post by vigs on 2011-01-07
> **1991sudarshan said:**
> Could you pls give more details regarding this issue do you want those packages show in the show in the attachment to removed or not to be upgraded?
I want those packages to upgrade. However, it says "Install these packages without verification", so there is some authentication issue that I am unable to resolve.

---

### Post by 1991sudarshan on 2011-01-07
you just try giving yes. If nothing happens just update using update manager and updating the os will be just a piece of cake and you won't be asked for any more authentication

---

### Post by vigs on 2011-01-07
> **1991sudarshan said:**
> you just try giving yes. If nothing happens just update using update manager and updating the os will be just a piece of cake and you won't be asked for any more authentication
Of course it works when I give yes - that is NOT the question I posted on the thread.

I want this warning to not come up - It started coming after I upgraded to maverick.
**Please reply iff you have any suggestions to remove this warning message.**

---

### Post by vigs on 2011-01-07
If it helps, here's the sources.list file:

[FONT=Courier New]# added by the release upgrader
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick main restricted
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates main restricted
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick universe
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick multiverse
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security main restricted
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security universe
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security multiverse
# deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/ # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) maverick main # disabled on upgrade to maverick
# deb-src [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) maverick main # disabled on upgrade to maverick
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-proposed restricted main multiverse universe
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-proposed restricted main multiverse universe #Added by software-properties
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-backports restricted main multiverse universe
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-backports restricted main multiverse universe #Added by software-properties
[/FONT]

---

### Post by 1991sudarshan on 2011-01-07
it seems that the files which you are trying to updates are the core essential libraries and files without them the os wont work properly and it is essential to get those warning while upgrading such files if my solution is not satisfactory why dont you try that question in icr !!

---

### Post by vigs on 2011-01-07
> **1991sudarshan said:**
> it seems that the files which you are trying to updates are the core essential libraries and files without them the os wont work properly and it is essential to get those warning while upgrading such files if my solution is not satisfactory why dont you try that question in icr !!
what's icr?

---

### Post by ajgreeny on 2011-01-07
You have some karmic-backports lines in sources.list that are not commented out and may be confusing the system.  Remove or comment them out and see if it helps.

---

### Post by vigs on 2011-01-07
> **ajgreeny said:**
> You have some karmic-backports lines in sources.list that are not commented out and may be confusing the system.  Remove or comment them out and see if it helps.
Phew!! Finally a sensible reply from someone :P
I tried that but still gives the same warning :(

---

### Post by presence1960 on 2011-01-07
> **vigs said:**
> Phew!! Finally a sensible reply from someone :P
I tried that but still gives the same warning :(

Just run the updates.

---

### Post by vigs on 2011-01-07
> **presence1960 said:**
> Just run the updates.
Useless post - does not answer my question.

---

### Post by presence1960 on 2011-01-07
> **vigs said:**
> Useless post - does not answer my question.

I think you are making a mountain out of nothing. Just run the updates. As long as they install who cares about the warning? As someone already mentioned you probably have backports and proposed updates enabled which can not be verified. **_[SIZE="7"]JUST RUN THE UPDATES!![/SIZE]_**You are being really piccune.

P.S. I have been getting those warnings since I started using Ubuntu in 2008, never had a problem- because I just run the updates. Get over it!

---

### Post by vigs on 2011-01-07
> **presence1960 said:**
> I think you are making a mountain out of nothing. Just run the updates. As long as they install who cares about the warning? As someone already mentioned you probably have backports and proposed updates enabled which can not be verified. **_[SIZE="7"]JUST RUN THE UPDATES!![/SIZE]_**You are being really piccune.

P.S. I have been getting those warnings since I started using Ubuntu in 2008, never had a problem- because I just run the updates. Get over it!
Useless post - does not answer my question.
FYI, using large fonts does not prove any point :)

---

### Post by presence1960 on 2011-01-07
> **vigs said:**
> Useless post - does not answer my question.
FYI, using large fonts does not prove any point :)

Not meant to prove a point but rather for emphasis. Again just run the updates or disable the repositories that are causing the message.

---

### Post by presence1960 on 2011-01-07
```
## [COLOR="Red"]N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/COLOR]
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick universe
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-updates universe

## [COLOR="Red"]N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team,[/COLOR] and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick multiverse
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-updates multiverse
```

Do I have to spell it out for you. Someone told you to disable these earlier- they are unsupported by ubuntu therefore can not be verified. But if you want to use the software they provide you will have to live with the message.

---

### Post by dfsmith on 2011-03-29
I also had this verification issue today.  It turned out that my apt-cacher-ng proxy was not working properly.  (Debian upgrade to squeeze on the proxy machine.)

And to anyone who says "just install the updates", I have a vital root certificate update for you: just ignore the warning about unknown origin....

---

