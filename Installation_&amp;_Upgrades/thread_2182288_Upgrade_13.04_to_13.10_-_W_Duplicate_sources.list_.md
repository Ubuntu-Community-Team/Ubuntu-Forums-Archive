---
title: "Upgrade 13.04 to 13.10 - W: Duplicate sources.list entry"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by dvanzo on 2013-10-20
Hi all!

After a very smooth upgrade, doing a sudo apt-get update shows a lot of duplicate entries... Already checked the sources.list file for duplicate entries without luck... Anybody?

Thanks in advance!

Daniel

Info:

W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/multiverse amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-updates/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-updates/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-backports/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-backports/multiverse amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-backports_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-backports/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-backports/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-security/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-security/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) saucy/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_saucy_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) saucy/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_saucy_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/webupd8team/themes/ubuntu/](http://ppa.launchpad.net/webupd8team/themes/ubuntu/) saucy/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_webupd8team_themes_ubuntu_dists_saucy_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/webupd8team/themes/ubuntu/](http://ppa.launchpad.net/webupd8team/themes/ubuntu/) saucy/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_webupd8team_themes_ubuntu_dists_saucy_main_binary-i386_Packages)

Sources.list file:
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) saucy main
# deb-src [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) raring main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy main multiverse

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-backports restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-backports restricted multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy-security restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

deb [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) saucy main 
deb-src [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) saucy main

---

### Post by Bashing-om on 2013-10-20
dvanzo; Hi !

check:
```

ls -la /etc/apt/sources.list.d

```
for additional source files. A likely suspect for duplicates.

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by dvanzo on 2013-10-21
> **Bashing-om said:**
> dvanzo; Hi !

check:
```

ls -la /etc/apt/sources.list.d

```
for additional source files. A likely suspect for duplicates.
[INDENT][INDENT]hope that helps
[/INDENT]
[/INDENT]


Result:

drwxr-xr-x 2 root root 4096 oct 19 20:19 .
drwxr-xr-x 6 root root 4096 oct 19 15:16 ..
-rw-r--r-- 1 root root  124 oct 19 13:41 jacob-media-saucy.list
-rw-r--r-- 1 root root  124 oct 19 13:41 jacob-media-saucy.list.save
-rw-r--r-- 1 root root  112 may 13 15:05 steam.list
-rw-r--r-- 1 root root  128 oct 19 13:41 tualatrix-ppa-saucy.list
-rw-r--r-- 1 root root  128 oct 19 13:41 tualatrix-ppa-saucy.list.save
-rw-r--r-- 1 root root    0 oct 19 13:40 ubuntu-x-swat-x-updates-saucy.list
-rw-r--r-- 1 root root    0 oct 19 13:40 ubuntu-x-swat-x-updates-saucy.list.save
-rw-r--r-- 1 root root  152 oct 19 13:41 webupd8team-y-ppa-manager-saucy.list
-rw-r--r-- 1 root root  152 oct 19 13:41 webupd8team-y-ppa-manager-saucy.list.save
-rw-r--r-- 1 root root  132 oct 19 13:41 xorg-edgers-ppa-saucy.list

---

### Post by Bashing-om on 2013-10-21
dvanzo; Hey;

On my closer inspection of your "/etc/apt/sources.list" index file, I see 7 duplications.
Are you comfortable editing files ?
Rather than enumerating all the dupes, how about using my "raring" file as a guide to what yours should be ?
Remember to make a backup of your current file prior to editing.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bad

```
and now to load the file into a text editor, gedit (the default editor)
```

gksudo gedit /etc/apt/sources.list

```
Be advised I have the "src" fetches commented out in my list as I have no need of source code in this install of mine. As well a few comments. If you are new to ubuntu you also have no need of those fetches either, you may safely and perhaps better comment them out too.
```

# deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted

# deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
#following line is a duplicate unknown why/where (24may2013) and commented out.
#deb http://security.ubuntu.com/ubuntu raring-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu raring-security main restricted
#(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
#(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
#(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#uncommented 23may2012
deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#uncommented 23may2013
deb http://extras.ubuntu.com/ubuntu raring main
# deb-src http://extras.ubuntu.com/ubuntu raring main

```
This is also a duplication in your list:
> 
deb [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) saucy main 
deb-src [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) saucy main
 the first reference I suggest you remove.

OK so far ? ...Now we are seeing the package manager screaming and hollering about amd64/i386 library mismatches. I will not be surprised if we have to remove a control file, and reload it. But lets see where we are  when the sources.list file is correct and:
```

sudo apt-get update
sudo apt-get upgrade

```
is done.

[INDENT][INDENT]this might get complicated
[/INDENT][/INDENT]

---

### Post by dvanzo on 2013-10-21
Thanks so much! With your guidance I can solve my problem!!! 

Regards,

Daniel

---

### Post by Bashing-om on 2013-10-21
dvanzo; good attitude !

Let me know when that last is completed and what results. Or if you experience problems.
We will carry on as required.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dvanzo on 2013-10-23
Bashing-om, people like you make using Ubuntu (and any other Linux distribution) an option for people like me... A big thanks!!!

Daniel

---

