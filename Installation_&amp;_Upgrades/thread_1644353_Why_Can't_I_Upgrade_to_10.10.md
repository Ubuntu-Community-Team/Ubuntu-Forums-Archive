---
title: "Why Can't I Upgrade to 10.10???"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by Nitrozzy7 on 2010-12-13
I'm asking this because this message pops up:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
Trying to install blacklisted version 'blcr-dkms_0.8.2-13'

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

----

As far as I know 10.10 is not a pre-released verion and I'm not running on a pre-released version either plus 10.10 isn't an unofficial software package.
So this means I ran into a bug? OK!
Where can I make a bug report?

---

### Post by zvacet on 2010-12-13
> Unofficial software packages not provided by Ubuntu


If you have any third party repos unchek them or put # sign in front of their lines in source list.

```
gksudo gedit /etc/apt/soutrces.list
```

after put # sign in front of third party repos save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

After that try to upgrade from update manageer.

---

### Post by Nitrozzy7 on 2010-12-13
No list appears. Still I unchecked the only one that was checked ([http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner) under the settings menu of the Update Manager but still the same message pops up.
I've tried checking/unchecking every single one bt stil the same.

It must be a bug.

---

### Post by Quackers on 2010-12-13
In a terminal try
```
sudo aptitude safe-upgrade
```
It may say you don't have aptitude installed but it will tell you how to install it in the error message, then run the above again.

---

### Post by Nitrozzy7 on 2010-12-13
Still nothing. Same message and my current version is still 10.04

---

### Post by Nitrozzy7 on 2010-12-13
How am I going to file a bug report?
By the way I've tried every command both of you provided but the only change was in the time it took for this message to appear. Now I'm just waiting a bit longer.
Ubuntu 10.04 ain't gonna cut it for me. I need the stable release.

---

### Post by wilee-nilee on 2010-12-13
I think your obsessed with a bug report, when a bug is not the problem.

So is this a regular install from a booted Ubuntu CD, or from inside a running windows environment?

10.04 is the long term release maverick is no more stable.

---

### Post by zvacet on 2010-12-14
@ [B]Nitrozzy7

[/B]> No list appears. 

Of course not.I mistyped command.It is

```
gksudo gedit /etc/apt/sources.list
```

You can also make this one your source list

> #deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse


---

### Post by Nitrozzy7 on 2010-12-14
@zvacet
Didn't work; still the same message.

@wilee-nilee
It is a regular install from a booted Ubuntu CD. My Laptop runs only on Ubuntu.
Note: things go downhill whenever I install a XX.04 release. I guess my laptop has a thing for XX.10 releases.

---

### Post by kansasnoob on 2010-12-14
That's due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/blcr/+bug/555729](https://bugs.launchpad.net/ubuntu/+source/blcr/+bug/555729)

Do you use "blcr-dkms"?

Package description:

> This package provides integration with the DKMS infrastructure for
automatically building out of tree kernel modules.

BLCR (Berkeley Lab Checkpoint/Restart) allows programs running on
Linux to be "checkpointed" (written entirely to a file), and then
later "restarted".

---

### Post by Nitrozzy7 on 2010-12-14
Now what? Is there a way to downgrade back to 9.10? Or I'll have to wait for the developers to fix it?
One more thing.
Yesterday I created an underprivileged "Guest" user and everything works fine and FAST. From Firefox to programs. Why is this happening and how can I make my root user work this way?

---

### Post by dino99 on 2010-12-14
clean your cache:

sudo rm /var/cache/apt/archives/*

then update/upgrade

---

### Post by Nitrozzy7 on 2010-12-14
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

This is what I get.

---

### Post by Nitrozzy7 on 2010-12-15
Seriously, my laptop does not work well with XX.04 releases for some reason. I need to Upgrade to 10.10. 
Every comand you provided to me resulted in a dead end. Honestly I'm not sure if any other command will do the trick; Still I need to Upgrade.

---

### Post by kansasnoob on 2010-12-15
Go to synaptic, then search for and remove the package blcr-dkms.

That should let you upgrade.

---

### Post by Nitrozzy7 on 2010-12-15
Aparently, it worked! There are still some speed related isues when I'm using my root user that need adressing, but at least I know I'm running on Ubuntu 10.10.
Thnx.

---

