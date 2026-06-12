---
title: "Unable to perform &quot;do-release-upgrade&quot; from 16.04 to 18.04 - No errors"
date: 2020-02-22
forum: Installation &amp; Upgrades
---

### Post by Vicious_Customs on 2020-02-22
Good day guys,
Apologies in advance for the long post, but I'm trying to do a release upgrade on my home server, and it's failing without cause. All apt packages are updated, and do-release-upgrade is simply aborting. Main and apt logs also show no errors. I've put a bit of information below in an effort to try and expose what may be causing the issue. I've pasted uname, lsb_release, my apt sources.list, the output of "do-release-upgrade", the "apt.log", and the "main.log". At this point I'm stumped. I'd really prefer to not have to nuke and pave and re-install if I can help it, so if anyone has any suggestions, I'm all ears. I've been searching for days, and I've tried just about everything I can find to no avail.

Thanks in advance! 

```
uname -a:
Linux jester 4.4.0-174-generic #204-Ubuntu SMP Wed Jan 29 06:41:01 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -a:
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial

$ sudo do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]
Get:2 Upgrade tool [1,242 kB]
Fetched 1,243 kB in 0s (0 B/s)
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg'
extracting 'bionic.tar.gz'


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Fetched 0 B in 0s (0 B/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done


Restoring original system state


Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done



$ cat /var/log/dist-upgrade/apt.log
Log time: 2020-02-22 16:04:55.491102
Log time: 2020-02-22 16:04:59.155892
Log time: 2020-02-22 16:05:05.053807

$ cat /var/log/dist-upgrade/main.log
2020-02-22 16:04:45,975 INFO Using config files '['./DistUpgrade.cfg.xenial']'
2020-02-22 16:04:45,975 INFO uname information: 'Linux jester 4.4.0-174-generic #204-Ubuntu SMP Wed Jan 29 06:41:01 UTC 2020 x86_64'
2020-02-22 16:04:46,509 INFO apt version: '1.2.32'
2020-02-22 16:04:46,509 INFO python version: '3.5.2 (default, Oct  8 2019, 13:06:37)
[GCC 5.4.0 20160609]'
2020-02-22 16:04:46,513 INFO release-upgrader version '18.04.36' started
2020-02-22 16:04:46,526 INFO locale: 'en_US' 'UTF-8'
2020-02-22 16:04:46,595 INFO screen could not be run
2020-02-22 16:04:46,744 DEBUG Using 'DistUpgradeViewText' view
2020-02-22 16:04:46,809 DEBUG enable dpkg --force-overwrite
2020-02-22 16:04:46,847 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2020-02-22 16:04:54,917 DEBUG lsb-release: 'xenial'
2020-02-22 16:04:54,917 DEBUG _pythonSymlinkCheck run
2020-02-22 16:04:54,918 DEBUG openCache()
2020-02-22 16:04:54,918 DEBUG No such plugin directory: ./plugins
2020-02-22 16:04:54,918 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2020-02-22 16:04:54,918 DEBUG plugins for condition 'bionicPreCacheOpen' are '[]'
2020-02-22 16:04:54,919 DEBUG plugins for condition 'from_xenialPreCacheOpen' are '[]'
2020-02-22 16:04:54,919 DEBUG quirks: running PreCacheOpen
2020-02-22 16:04:54,919 DEBUG running Quirks.PreCacheOpen
2020-02-22 16:04:55,734 DEBUG /openCache(), new cache size 90991
2020-02-22 16:04:55,734 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2020-02-22 16:04:55,734 DEBUG checkViewDepends()
2020-02-22 16:04:55,735 DEBUG running doUpdate() (showErrors=False)
2020-02-22 16:04:58,528 DEBUG openCache()
2020-02-22 16:04:59,409 DEBUG /openCache(), new cache size 90991
2020-02-22 16:04:59,409 DEBUG doPostInitialUpdate
2020-02-22 16:04:59,409 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2020-02-22 16:04:59,409 DEBUG plugins for condition 'bionicPostInitialUpdate' are '[]'
2020-02-22 16:04:59,409 DEBUG plugins for condition 'from_xenialPostInitialUpdate' are '[]'
2020-02-22 16:04:59,409 DEBUG quirks: running bionicPostInitialUpdate
2020-02-22 16:04:59,409 DEBUG running Quirks.bionicPostInitialUpdate
2020-02-22 16:05:04,428 DEBUG abort called
2020-02-22 16:05:04,429 DEBUG openCache()
2020-02-22 16:05:05,295 DEBUG /openCache(), new cache size 90991

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


#deb [http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/) lsb3.2 main
```

---

### Post by wildmanne39 on 2020-02-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by wildmanne39 on 2020-02-22
I am sure the reason it fails is because 14.04 reached EOL April 2019 and you can not easily upgrade an EOL version once the repositories have been removed.

It is best to back up all important data and do a fresh install, I understand this is not always the desired method when dealing with a server though.

There is a way but it is painful and may create issues, I do not recommend it.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Impavidus on 2020-02-23
The only reference to 14.04 is the disabled repository from the live disk. It appears this 16.04 system was originally installed as 14.04 and later upgraded.

I see a disabled epson repository. Maybe you installed proprietary printer drivers or something like that. Such packages may block upgrades. Remove all packages that are not from the official repositories and try again.

On the other hand, you already spent days to fix this. Would a fresh install really take more time than that?

---

### Post by TheFu on 2020-02-23
The **do-release-upgrade** didn't change the repositories.  Perhaps it didn't disable all the PPAs in /etc/apt/sources.list.d/.
You can manually do both of those, then run 
```
sudo apt update
sudo apt full-upgrade

```and take your chances.  Ask if you need help doing either.  I would just **rename** the PPA files and a global search/replace for the main *sources.list* file with vim/sudoedit.

Once a release upgrade failed here because my personal environment had a different version of perl active.  The system perl was untouched and where it belonged. A lazy systems dev didn't force the system perl to be used. He trusted the PATH.  Bad, bad, dev.  Never trust the PATH in scripts. NEVER!

Obviously, these are high-risk things.  Backup anything you can't lose first.

---

### Post by Vicious_Customs on 2020-02-23
Thanks, guys! I appreciate it.

I'll definitely use the code tags going forward. Apologies for making it harder than it had to be.  

Yes, this did indeed start as a 14.04 system many moons ago and was upgraded. I've also swapped out all the hardware along the way. The epson printer is long gone, and the repo was commented out when it began failing as it's no longer maintained. I'll go through and remove anything that I can remember installing and try again. If that doesn't work, I'll attempt the full-upgrade after changing the repos. I did that before quite some time ago on a debian install, so I'm familiar with what's being suggested. Good backups keep me from pulling my hair out, so if that doesn't work I'll have no choice but to re-install. That will force me to have to re-setup my system, which will suck, but such is life. 

Again, much appreciated. I'll report back when I've completed the process.

---

### Post by TheFu on 2020-02-23
Many things have changed in 18.04, so you will need to reconfigure those anyway.  New versions of apache, mariadb, samba, CUPS, different DEs with different config, no more ifupdown - netplan is the new network config method, and snaps are coming whether we want them or not.

If you capture a list of manually installed programs now, then you can feed that list back into the 18.04 APT and get almost all of those installed at one time.  If you plan to go this direction, best to put the data and system configs for those specific daemons back BEFORE doing the package install.  Most the the "re-setup" should be done within about 45 of beginning the install.  Only huge data, like media files will make the restore longer.

---

### Post by Vicious_Customs on 2020-03-20
Hey guys, sorry for the delay here. I was able to do the update by modifying the sources.list and changing it to bionic. It took a bit of tinkering, running apt-get upgrade / dist-upgrade / fix-broken a half dozen times, but eventually everything returned clean. Once that was done I rebooted and was pleasantly surprised to see it boot with no troubles. I did have a little additional configuration to do, but all is well. 

Disclaimer: this worked for me, but I have no idea how it might work for someone else. I am no expert, so don't take what I did as a good solution. I would definitely recommend anyone else who might want to try this ensure they have a good backup before proceeding.

---

