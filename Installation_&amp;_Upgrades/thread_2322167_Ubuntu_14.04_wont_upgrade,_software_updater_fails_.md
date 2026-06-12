---
title: "Ubuntu 14.04 wont upgrade, software updater fails to connect to internet"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by Tarhawk on 2016-04-26
I am trying to start the process of upgrading from _*14.04*_ to 14.10, to 15. to the latest version on a_* Toshiba Satellite C-55b*_. 

I have internet connectivity, evidenced by this message from the very same computer.  OS will also download updates, just not upgrades.

I have tried a number of workarounds I have found researching the issue, but still my problem persists.

Any help would be great,

**The error message and output details read as follows:**
[I]Failed to download repository information.
Check your internet connection.

Details
[/I]```
W:Failed to fetch cdrom://Ubuntu 14.04.3 LTS _utopic Tahr_ - Beta amd64 (20150805)/dists/utopic/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.3 LTS _utopic Tahr_ - Beta amd64 (20150805)/dists/utopic/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.3 LTS _utopic Tahr_ - Beta amd64 (20150805)/dists/utopic/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.3 LTS _utopic Tahr_ - Beta amd64 (20150805)/dists/utopic/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/main/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.26 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2016-04-26
How far into trying to get to 14.10 did you get?

---

### Post by Tarhawk on 2016-04-26
The thing is, I read that upgrading from one lts to another, it is necessary to go through each release.  However, when the prompt comes up to upgrade to a new version of Ubuntu it says it is upgrading to 15.10lts, not to 14.10.  I have tried the workarounds to get it to switch to 14.10 but so far it just produces the same error.  Beyond the initial stages I cannot proceed with the upgrade because of this error.

---

### Post by deadflowr on 2016-04-26
Why didn't you take the prompt for 15.10?
It's there for a reason.
You can then upgrade from that to 16.04 if you want.
No need to upgrade from 14.04 to 14.10 to 15.04 to 15.10 to 16.04, anymore.

Also: You can upgrade from 14.04 to 16.04.
It's just that you cannot officially do so at the moment.
That ability will come some time around late July.
When 16.04.1, the first point release is out.

You can, however upgrade from 14.04 to 16.04 unofficially by using the development flag running update-manager from a command line:
```
update-manager -d
```
Beware that this method is still under construction, so to speak. So it can be unstable or broken at any given time.

What it would look like:
[ATTACH=CONFIG]268647[/ATTACH]

I really think that if you haven't gotten 14.10 installed, it would best to revert the sources.list back to 14.04.
Here's my 14.04 sources.list to help
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
```

It's pretty much default, I'd comment or uncomment  what you might usually have, if anything. (# symbol in front of any line means it is commented out = will not be read)

Then either upgrade to 15.10, and then 16.04 or you can try the development flag and risk that method.

I would recommend, which ever way you choose, BACKUP the files that you really need. 
(Most users simply backup the whole Home folder, but to each his own)

Better safe than sorry.

---

### Post by Tarhawk on 2016-04-27
I did try to do the upgrade directly to the 15.10, but it produced the same error message.

I am a novice user of linux.  I would like to try to revert the source list back to 14.04 but I am not sure exactly where or how I would do that, or where I would copy the source list you posted to.  Forgive my linux ignorance here.

---

