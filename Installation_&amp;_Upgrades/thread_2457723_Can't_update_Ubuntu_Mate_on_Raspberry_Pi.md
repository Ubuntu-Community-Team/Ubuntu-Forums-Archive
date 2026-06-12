---
title: "Can't update Ubuntu Mate on Raspberry Pi"
date: 2021-02-07
forum: Installation &amp; Upgrades
---

### Post by furtom on 2021-02-07
I'm running Mate 20.10 on Ras Pi (arm64). APT seems to be telling me [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) is down, which I know isn't true.

When I run ```
sudo apt update
``` I get:

```
  404  Not Found [IP: 91.189.91.38 80]
Fetched 483 kB in 1s (358 kB/s)
Reading package lists... Done
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/groovy/main/binary-arm64/Packages  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/groovy-updates/main/binary-arm64/Packages  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/groovy-backports/universe/binary-arm64/Packages  404  Not Found [IP: 91.189.91.38 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

This doesn't add up. I also checked the server with my browser and all seems well.

The contents of my sources.list file:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ groovy main restricted
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ groovy-updates main restricted
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ groovy universe
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy universe
# deb http://us.archive.ubuntu.com/ubuntu/ groovy-updates universe
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ groovy multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ groovy-updates multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ groovy-backports main restricted universe multiverse

```

Anything that can steer me in the right direction would be appreciated.

---

### Post by ActionParsnip on 2021-02-07
If you change package source does it help?

---

### Post by furtom on 2021-02-07
That was my first thought, but I can't find an alternative repo. It seems most mirrors don't yet host arm64.

---

### Post by furtom on 2021-02-08
Well, this turned out to be stupid...

My sources.list was completely wrong. All the entries that begin with address "http://us.archive.ubuntu.com" are destined to fail as that repo doesn't have an arm64 release!

The only correct repos for Raspberry Pi begin with "http://ports.ubuntu.com".

The correct source.list file should read:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ groovy main restricted
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ groovy-updates main restricted
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ groovy universe
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy universe
deb http://ports.ubuntu.com/ubuntu-ports/ groovy-updates universe
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ groovy multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ groovy-updates multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ groovy-backports main restricted universe multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu groovy partner
# deb-src http://archive.canonical.com/ubuntu groovy partner

deb http://ports.ubuntu.com/ubuntu-ports/ groovy-security main restricted
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ groovy-security universe
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ groovy-security multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ groovy-security multiverse

```

The error was introduced in the Software & Updates utility. I had tried to change the Download from: entry from "Main server" to "Server for United States" in an effort to find a closer mirror. DO NOT DO THIS!

At this time, this utility does not perform as expected. It instead changes sources to non functioning, but good looking, "us.archive.ubuntu.com." This is an oversight by the developers and I'll file a bug.

Thanks every one for the attention!

---

### Post by guiverc on 2021-02-08
I just saw your post and was going to say that..  (*just opening thread*)
I assumed you'd manually changed the mirror though (to one on [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) for example) and not used an inbuilt tool :(


Because you used an inbuilt tool, I'd recommend you file a bug using `ubuntu-bug <package>'.


I'm not sure what the package could be; I'd likely

```
dpkg -l |grep software
```

to see what is there, `gnome-software` comes to mind, but I don't have a Ubuntu-MATE system handy to look  A look at [https://packages.ubuntu.com/groovy/ubuntu-mate-desktop](https://packages.ubuntu.com/groovy/ubuntu-mate-desktop) though implies to me it's likely `software-properties-gtk` that it should be filed against ([https://packages.ubuntu.com/groovy/software-properties-gtk](https://packages.ubuntu.com/groovy/software-properties-gtk)), ie. my guess is the command to file the bug is

```
ubuntu-bug software-properties-gtk
```

I'll provide the standard link for filing bugs too - [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

If you don't want to file that way, the next option I'd likely use is mentioning it on the Ubuntu-MATE discourse ([https://ubuntu-mate.community/](https://ubuntu-mate.community/)) as they allow bugs to be filed there. It's really a common Ubuntu package issue I believe (*not just impacting Ubuntu-MATE I'd bet*) so it'll get need to be filed on launchpad eventually.

Well done for working it out though.

---

### Post by furtom on 2021-02-09
[QUOTE= guiverc]Because you used an inbuilt tool, I'd recommend you file a bug using `ubuntu-bug <package>'.[/QUOTE]

Exactly! It's also why it took me a while to catch on. I never imagined this would be the case and was looking for more unusual solutions in my apt.conf and the like.

Thanks for your help!

---

