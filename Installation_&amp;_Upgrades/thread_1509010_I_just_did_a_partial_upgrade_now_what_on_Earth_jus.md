---
title: "I just did a partial upgrade now what on Earth just happened (screenshots)"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by wilwil0 on 2010-06-13
I was using 9.10. My Update Manager recommended a partial upgrade. I did it, then restarted so that the updates could take effect.

Now my desktop has transformed into this Windows 98 style monstrosity

[http://tinypic.com/view.php?pic=ab3vnl&s=6](http://tinypic.com/view.php?pic=ab3vnl&s=6)

Yes I'm sure I upgraded correctly, yes I have got a CD of 10.04 LTS I can simply install over. 

But what has happened?
How do I upgrade it fully?

---

### Post by MCVenom on 2010-06-13
Not sure at all *how* your Gnome layout got changed, but obviously it's not good (in your situation, anyway :P).

I don't know about upgrading from one stable release to another, but I do know the conventional wisdom when installing upgrades on development versions of Ubuntu is to _**never**_ install a partial upgrade; it's usually an indicator that something is very wrong. Did you have any PPAs or out of repo software on your system?

---

### Post by wilwil0 on 2010-06-13
No PPA's.

If by out of repo software you mean stuff installed that isn't in the repository then yes: Spotify, but nothing else. I did install iTUnes, but have already uninstalled it as I preferred some stuff in the repository.

I've just tried running the Upgrade Manager and it came up with this:

[http://tinypic.com/view.php?pic=sl385g&s=6](http://tinypic.com/view.php?pic=sl385g&s=6)

Mean anything?

---

### Post by MCVenom on 2010-06-13
> **wilwil0 said:**
> No PPA's.

If by out of repo software you mean stuff installed that isn't in the repository then yes: Spotify, but nothing else. I did install iTUnes, but have already uninstalled it as I preferred some stuff in the repository.

I've just tried running the Upgrade Manager and it came up with this:

[http://tinypic.com/view.php?pic=sl385g&s=6](http://tinypic.com/view.php?pic=sl385g&s=6)

Mean anything?
Well, I don't really know what other cause there would be other than third party repos, and the picture you posted seems to confirm that some were enabled... Could you run this command and paste the output?

```
cat /etc/apt/sources.list
# Prints what software sources are on your system
```

---

### Post by wilwil0 on 2010-06-13
And now this, eek!

[http://tinypic.com/view.php?pic=2z56jhu&s=6](http://tinypic.com/view.php?pic=2z56jhu&s=6)

---

### Post by wilwil0 on 2010-06-13
Results

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100318)]/ lucid main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

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
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe

# deb [http://packages.deepin.org](http://packages.deepin.org) lucid main # disabled on upgrade to lucid
# deb [http://linux.dropbox.com](http://linux.dropbox.com) lucid main # disabled on upgrade to lucid
# deb [http://download.virtualbox.org](http://download.virtualbox.org) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid main # disabled on upgrade to lucid
# deb [http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release](http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release) lucid main # disabled on upgrade to lucid


---

### Post by wilwil0 on 2010-06-13
I'm guessing that these: 

> # deb [http://packages.deepin.org]("http://packages.deepin.org/")  lucid main # disabled on upgrade to lucid
# deb [http://linux.dropbox.com]("http://linux.dropbox.com/")  lucid main # disabled on upgrade to lucid
# deb [http://download.virtualbox.org]("http://download.virtualbox.org/")  lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid main # disabled on upgrade to lucid
# deb [http://download.virtualbox.org/virtu...karmic/Release]("http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release")  lucid main # disabled on upgrade to lucid

are third party, I may be wrong about there being no PPA's or other third party software.

I don't see why that would change the very layout however...

---

### Post by MCVenom on 2010-06-13
> **wilwil0 said:**
> I'm guessing that these: 



are third party, I may be wrong about there being no PPA's or other third party software.

I don't see why that would change the very layout however...
Yep, those are probably the culprits. My advice at this point would be to just do a clean reinstall.

---

### Post by wilwil0 on 2010-06-14
Thank you for the advice but I found a different solution (I'll just put it here in case anyone gets the same problem.

On the GRUB thing at the start I picked the latest edition recovery mode, then chose the option to fix all packets.

I then restarted and at the menu for logging in could now change the Layout from Xcfe (or something like that) to GNOME. Seems so simple now that I wonder how I missed it. I don't remember changing anything on that menu though so it must be something to do with the preferences being changed after doing a partion upgrade.

---

