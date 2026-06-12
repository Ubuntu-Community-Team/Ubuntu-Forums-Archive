---
title: "Issue Updating Ubuntu 16.04"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by SBTlauien on 2017-10-20
I'm running Ubuntu 16.04.2 LTS and I am getting the following errors while updating. How can I fix this issue? I've searched and it looks like I need to remove Ubuntu-Tweak, which I didn't know I even had installed. The problem is that I don't know how to remove it. I tried removing the ppa but the response says that it's not installed.

```
Reading package lists... Error!
W: The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_multiverse_i18n_Translation-en (1)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted
```

Trying this...

sudo add-apt-repository --remove ppa:tualatric/ubuntu-tweak

...gives...

```
Cannot add PPA: 'ppa:~tualatric/ubuntu/ubuntu-tweak'.
ERROR: '~tualatric' user or team does not exist.
```

:confused:

---

### Post by Autodave on 2017-10-20
If it actually does not exist, then you need to remove it from the list.  Does it exist still?

---

### Post by ian-weisser on 2017-10-20
> **SBTlauien said:**
> sudo add-apt-repository --remove ppa:**tualatric**/ubuntu-tweak

It's misspelled.

---

### Post by SBTlauien on 2017-10-20
> **ian-weisser said:**
> It's misspelled.

Oops.  Well, after correcting that spelling, it worked but I'm still getting the exact same message when I try to update.

It looks as if that command isn't even removing the ppa.  I can run that command over and over again and I still get the "Press [ENTER] to continue or ctrl-c to calcel removing it" prompt.  I press ENTER every time.

---

### Post by dino99 on 2017-10-20
> **SBTlauien said:**
> Oops.  Well, after correcting that spelling, it worked but I'm still getting the exact same message when I try to update.

It looks as if that command isn't even removing the ppa.  I can run that command over and over again and I still get the "Press [ENTER] to continue or ctrl-c to calcel removing it" prompt.  I press ENTER every time.

I wonder if you understand what you are doing :lolflag:
Why not checking yourself that ppa: you easily could see that it has not been updated since Trusty; so there is no more recent version ;)
Then why using an outdated ppa when the ubuntu archive have a similar maintained app (search with 'synaptic')

If you have added yourself that ppa, then you might know how to remove it (in case you also ignore that, then use ppa-purge)

---

### Post by ian-weisser on 2017-10-20
> **SBTlauien said:**
> Well, after correcting that spelling, it worked but I'm still getting the exact same message when I try to update.

I'm not sure what you mean by 'it worked'. Did it remove any packages installed on your system?
If so, then simply locate and delete the source entry in /etc/apt/sources.list*. It's just a line of text or a single tiny file in there.
Then run an 'apt update' to refresh your package database because your sources have changed.

Then try again to see if that particular error is solved, 
Then we'll move on to the next problem.

---

### Post by SBTlauien on 2017-10-20
> **dino99 said:**
> I wonder if you understand what you are doing :lolflag:
Why not checking yourself that ppa: you easily could see that it has not been updated since Trusty; so there is no more recent version :wink:
Then why using an outdated ppa when the ubuntu archive have a similar maintained app (search with 'synaptic')

If you have added yourself that ppa, then you might know how to remove it (in case you also ignore that, then use ppa-purge)

This is something that I must have accidentely added a while back.  I'm not even using Ubuntu-Tweak, I'm using Unity-Tweak.

I don't have ppa-purge installed and when I try installing it, get this...

sudo apt-get install ppa-purge

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 armory : Depends: python-qt4 but it is not going to be installed
          Depends: python-twisted but it is not going to be installed
          Depends: python-psutil but it is not going to be installed
 easytether:i386 : Depends: libbluetooth3:i386 (>= 4.91) but it is not going to be installed
                   Depends: libc6:i386 (>= 2.16) but it is not going to be installed
                   Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not going to be installed
                   Depends: resolvconf:i386
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

> **ian-weisser said:**
> I'm not sure what you mean by 'it worked'. Did it remove any packages installed on your system?
If so, then simply locate and delete the source entry in /etc/apt/sources.list*. It's just a line of text or a single tiny file in there.
Then run an 'apt update' to refresh your package database because your sources have changed.

Then try again to see if that particular error is solved, 
Then we'll move on to the next problem.

I'm not 100% sure if it removed anything or not.  The command didn't give me any errors after running it, but I am still getting the same error when I try to update.  So I asume that it didn't actually remove anything.

It's not in "/etc/apt/sources.list*", this is what is in that file...

```

# deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports universe main restricted multiverse

```

---

### Post by dino99 on 2017-10-20
List the ppa(s) with:
> sudo software-properties-gtk

---

