---
title: "Saucy does not see Trusty as a new release"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by linux-klomp on 2014-09-26
```

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

```
I've done update, upgrade and dist-upgrade.
```

~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
No new release found

```
it should look for LTS
```

~$ cat /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts

```
Why is it not finding Trusty ?
](*,)

I don't think I've left anything non-saucy active...
```
:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy universe
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu saucy main
# deb-src http://extras.ubuntu.com/ubuntu raring main

## virtualbox
# deb http://download.virtualbox.org/virtualbox/debian saucy contrib

# Logitech Media Server
### deb http://debian.slimdevices.com stable main


```

---

### Post by deadflowr on 2014-09-26
I think you need to change the sources from archive to old-release.
Try this
first make a quick backup for fallback reason, in case something goes boing.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
then run
```
sudo sed -i -e 's/ca.archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
```
then reload it with
```
sudo apt-get update
```
then try the do-release-upgrade command.

It should allow the upgrade then. Don't know how well it'll go, but good luck.

EDIT: oh I should also probably add the normal mantra, make sure you have backups of all your important data, in case things go awry.

---

### Post by linux-klomp on 2014-09-27
Thank you for the suggestion.

However it did not work. Was curious what system should have changed the sources file, if it was the solution...
```

~$ sudo apt-get update 
Ign http://old-releases.ubuntu.com saucy InRelease
Ign http://old-releases.ubuntu.com saucy-updates InRelease
Ign http://old-releases.ubuntu.com saucy-backports InRelease
Ign http://old-releases.ubuntu.com saucy-security InRelease
Ign http://old-releases.ubuntu.com saucy Release.gpg
Ign http://old-releases.ubuntu.com saucy-updates Release.gpg
Ign http://old-releases.ubuntu.com saucy-backports Release.gpg
Ign http://old-releases.ubuntu.com saucy-security Release.gpg
Ign http://old-releases.ubuntu.com saucy Release
Ign http://old-releases.ubuntu.com saucy-updates Release
Ign http://old-releases.ubuntu.com saucy-backports Release
Ign http://old-releases.ubuntu.com saucy-security Release
Err http://old-releases.ubuntu.com saucy/main Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy/restricted Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy/universe Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy/multiverse Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy/main amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com saucy/main Translation-en_CA
Ign http://old-releases.ubuntu.com saucy/main Translation-en
Ign http://old-releases.ubuntu.com saucy/multiverse Translation-en_CA
Ign http://old-releases.ubuntu.com saucy/multiverse Translation-en
Ign http://old-releases.ubuntu.com saucy/restricted Translation-en_CA
Ign http://old-releases.ubuntu.com saucy/restricted Translation-en
Ign http://old-releases.ubuntu.com saucy/universe Translation-en_CA
Ign http://old-releases.ubuntu.com saucy/universe Translation-en
Err http://old-releases.ubuntu.com saucy-updates/main Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/restricted Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/universe Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/multiverse Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/main amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com saucy-updates/main Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-updates/main Translation-en
Ign http://old-releases.ubuntu.com saucy-updates/multiverse Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-updates/multiverse Translation-en
Ign http://old-releases.ubuntu.com saucy-updates/restricted Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-updates/restricted Translation-en
Ign http://old-releases.ubuntu.com saucy-updates/universe Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-updates/universe Translation-en
Err http://old-releases.ubuntu.com saucy-backports/main Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/restricted Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/universe Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/multiverse Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/main amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-backports/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com saucy-backports/main Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-backports/main Translation-en
Ign http://old-releases.ubuntu.com saucy-backports/multiverse Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-backports/multiverse Translation-en
Ign http://old-releases.ubuntu.com saucy-backports/restricted Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-backports/restricted Translation-en
Ign http://old-releases.ubuntu.com saucy-backports/universe Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-backports/universe Translation-en
Err http://old-releases.ubuntu.com saucy-security/main Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/restricted Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/universe Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/multiverse Sources
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/main amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com saucy-security/main Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-security/main Translation-en
Ign http://old-releases.ubuntu.com saucy-security/multiverse Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-security/multiverse Translation-en
Ign http://old-releases.ubuntu.com saucy-security/restricted Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-security/restricted Translation-en
Ign http://old-releases.ubuntu.com saucy-security/universe Translation-en_CA
Ign http://old-releases.ubuntu.com saucy-security/universe Translation-en
W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/main/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/restricted/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/universe/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/main/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/restricted/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/universe/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/restricted/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/universe/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
~$  sudo do-release-upgrade -d
Checking for a new Ubuntu release
No new release found

```

---

### Post by deadflowr on 2014-09-27
Did you move the old version back?
(Or simple copy the output from you earlier post and save it as the filename)
reversing course as it were.
Then, maybe, also try changing the release-upgrade from Prompt=lts to Prompt = normal, and then run the apt-get update command again.
See what happens then...

---

### Post by oldos2er on 2014-09-27
Run ```
do-release-upgrade
``` without the -d option, which tells the upgrade software to look for a development version (which as of this date would be utopic 14.10).

---

### Post by linux-klomp on 2014-09-29
```

~$ sudo apt-get update  
Ign http://security.ubuntu.com saucy-security InRelease
Ign http://ca.archive.ubuntu.com saucy InRelease
Hit http://security.ubuntu.com saucy-security Release.gpg
Ign http://ca.archive.ubuntu.com saucy-updates InRelease
Hit http://security.ubuntu.com saucy-security Release
Ign http://ca.archive.ubuntu.com saucy-backports InRelease
Hit http://security.ubuntu.com saucy-security/main Sources
...
Ign http://ca.archive.ubuntu.com saucy-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com saucy-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com saucy-backports/universe Translation-en_CA
Reading package lists... Done
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
```
Still nothing...

Can I just change saucy to trusty in the sources list as last resort?
Or would that break something?

---

### Post by linux-klomp on 2014-09-29
> **deadflowr said:**
> 
Then, maybe, also try changing the release-upgrade from Prompt=lts to Prompt = normal, and then run the apt-get update command again.
Did not help, still nothing to upgrade... ](*,)

---

### Post by madtom1999 on 2014-09-29
I had this on two machines - are you expecting LTS releases? Change the setting to any old recommended release and try again.

---

### Post by linux-klomp on 2014-09-29
> **madtom1999 said:**
> I had this on two machines - are you expecting LTS releases? Change the setting to any old recommended release and try again.
Trusty is the next release for Saucy and it happens to be an LTS release. 
What I expect is to get the question if I want to upgrade.

Are you saying to revert back to Precise to see if it will upgrade?

What would happen if I manually change the sources.list to Trusty?

---

### Post by ian-weisser on 2014-09-29
What is the last line of /etc/update-manager/release-upgrades ?

Also see several possible things to check at [http://askubuntu.com/questions/124999/distribution-upgrade-problem-no-new-release-found](http://askubuntu.com/questions/124999/distribution-upgrade-problem-no-new-release-found)

---

### Post by linux-klomp on 2014-10-01
> **ian-weisser said:**
> What is the last line of /etc/update-manager/release-upgrades ?
As in my OP```
Prompt=lts
```
>  Also see several possible things to check at [http://askubuntu.com/questions/124999/distribution-upgrade-problem-no-new-release-found](http://askubuntu.com/questions/124999/distribution-upgrade-problem-no-new-release-found) 
Thanks, checking this out... :-\"

---

### Post by linux-klomp on 2014-10-02
OK seems the link got me somewhere.=d>

Since I'm not on LTS, I need to change */etc/update-manager/release-upgrades *
```
Prompt=normal
```
Then run
```
sudo do-release-upgrade 
```
I thought I had already tried that, but this time it seems to recognize Trusty :-D
(aborted, since I tried from an ssh session.)
It's just too late to do it now, but will report bac,k if this is going to be successful. O:)

---

### Post by linux-klomp on 2014-12-31
Sorry for not reporting back earlier, but the ```
Prompt=normal
``` did the trick!

:p

---

