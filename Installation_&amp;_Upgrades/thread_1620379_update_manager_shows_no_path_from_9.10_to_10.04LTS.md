---
title: "update manager shows no path from 9.10 to 10.04LTS"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by Paper Pusher on 2010-11-13
I'm upgrading my machines UDTE-64 from 9.10 to 10.4LTS.  9.10 is working fine.  I just want to upgrade to a current LTS release.
Update manager showed the way on one desktop and I upgraded successfully.
On another desktop and a laptop, update manager does not show that a new release is available.
What's going on?
It's fair game to tell me to use the live cd so long as I preserve user data.

---

### Post by sikander3786 on 2010-11-13
Try

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

and then

```
update-manager -d
```

If it still doesn't show the new release, make sure no repositories are disabled under System > Administration > Software Sources.

If still can't figure it out, please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by Paper Pusher on 2010-11-13
```
cat /etc/apt/sources.list# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

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
deb http://security.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe


```

---

### Post by sikander3786 on 2010-11-13
Nothing offensive I could find in that output except

> deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

Go to System > Administration > Software Sources and uncheck the entry for CD-ROM.

Or edit your /etc/apt/sources.list by

```
gksudo gedit /etc/apt/sources.list
```

And put a # infront of above mentioned line.

Update,

```
sudo apt-get update
```

Start Update Manager by,

```
update-manager -d
```

If it still doesn't list the new distro, try from command line with,

```
sudo apt-get dist-upgrade

```

---

### Post by Paper Pusher on 2010-11-13
Thank you for the suggestions.  I tried them all.   Unfortunately, none of them changed things.  Update manager does not suggest a new release.

I have posted the sources file.

---

### Post by Paper Pusher on 2010-11-13
I apologize, but nothing worked.

---

