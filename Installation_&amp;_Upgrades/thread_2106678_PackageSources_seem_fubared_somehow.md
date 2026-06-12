---
title: "Package/Sources seem fubared somehow?"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by blortuga on 2013-01-19
I noticed this problem when I was trying to install the updated AMD Catalyst 13.1 driver.

(running 64-bit 12.10 on a Dell Inspiron laptop)

The installation prerequisite says I need to install cdbs and dh-make. When I tried to install these I got: "package cdbs has no installation candidate".

I had already done the uninstall of the previous driver (fglrx) - so I had to reinstall that when I rebooted in order to get my graphical environment back. (also had to re-install ubuntu-desktop).  

Now, when I try to get into Software Center sources, absolutely nothing happens - the app just does not appear.  When I try to use Synaptic Package Manager, and check Settings->Repositories - it says "Repositories Changed, click the Reload button" and it goes through the reload rigamarole, but it won't let me select my repositories.

When I run apt-get upgrade and apt-get update, there aren't any errors.  

I can't select "cdbs" or "dh-make" through Synaptic at all. They're just not there.

I'm really confused, because I'm not really getting any actionable errors, but things are not working, so I believe that I have a misconfigured set of packages somehow.

---

### Post by blortuga on 2013-01-19
This is my /etc/apt/sources.list:

```

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates restricted multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://us.archive.ubuntu.com/ubuntu/ quantal-security restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-security restricted multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ quantal-security universe
deb http://us.archive.ubuntu.com/ubuntu/ quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
# deb http://archive.ubuntu.com/ubuntu/ precise proposed
# deb-src http://archive.ubuntu.com/ubuntu/ precise proposed #Added by software-properties
# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu quantal main # disabled on upgrade to quantal
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu quantal main # disabled on upgrade to quantal
# deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu quantal main # disabled on upgrade to quantal
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu quantal main # disabled on upgrade to quantal
# deb http://ppa.launchpad.net/ferramroberto/java/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ferramroberto/java/ubuntu oneiric main

# ppa's for darktable:
# deb http://ppa.launchpad.net/pmjdebruijn/darktable-release-plus/ubuntu quantal main # disabled on upgrade to quantal
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release-plus/ubuntu quantal main # disabled on upgrade to quantal

# ppa's for the new dell xps13 and xps15 drivers (11.2012)
# deb http://ppa.launchpad.net/canonical-hwe-team/sputnik-kernel/ubuntu quantal main # disabled on upgrade to quantal
# deb-src http://ppa.launchpad.net/canonical-hwe-team/sputnik-kernel/ubuntu quantal main # disabled on upgrade to quantal


```

---

### Post by oldos2er on 2013-01-19
Go into your Software Sources and enable the main repository. Once that's done, run ```
sudo apt-get update && sudo apt-get install cdbs
```

---

### Post by blortuga on 2013-01-19
Thank you for the response.
(my system is mostly operational, for now, but it is kind of worrisome that I am potentially not able to install software now).

I can't get into software sources?!

Launcher->Software Sources -> ...... nothing

Seems like the same symptoms as THIS thread:
[http://ubuntuforums.org/showthread.php?t=2077871](http://ubuntuforums.org/showthread.php?t=2077871)

. . . however, I opened /var/lib/dpkg/status in gedit, and received no unicode error.

(so. . . apparently Software Sources is actually *crashing* on me - I have a crash report, but the dang dialog doesn't let me copy actual text. Whose idea was that? I can "send a report")

Anyway - it's close because the problem is "software-properties-gtk crashed with KeyError in __getitem__():" and the traceback says the most recent call goes to a KeyError: 'xserver-xorg-video-ati' . . . which sounds suspiciously related to all the other issues I'm dealing with.

So - I can't fix my Software Sources problem, because I can't run it, because it relies on software-properties-gtk being able to getitem() from the xserver-xorg-video-ati key (of some configuration file) . . . does that sound right?  

One area that I'm not very knowledgeable about is how to configure xorg. . .  from a usability perspective, it basically seems to just take care of itself, but when I try to read about how to configure it, there are so many options I don't know what applies or not.

---

### Post by deadflowr on 2013-01-19
In 12.10 go to system setting and software settings is in there.

Or in a terminal type

```
software-properties-gtk
```

I believe it's can also be found in the software centers menu somewhere.

---

### Post by blortuga on 2013-01-19
when I run;
sudo software-properties-gtk, this is the set of errors I get;
```

(software-properties-gtk:4675): IBUS-WARNING **: The owner of /home/username/.config/ibus/bus is not root!
gpg: /tmp/tmpzjqw21/trustdb.gpg: trustdb created
WARNING: a driver (xserver-xorg-video-ati) doesn't have any available package associated: {'builtin': True, 'from_distro': True, 'free': True, 'recommended': True}
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 178, in __getitem__
    return self._weakref[key]
  File "/usr/lib/python3.2/weakref.py", line 69, in __getitem__
    o = self.data[key]()
KeyError: 'xserver-xorg-video-ati'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 179, in __init__
    self.show_drivers()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1302, in show_drivers
    self.set_driver_action_status()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1326, in set_driver_action_status
    pkg = self.apt_cache[pkg_name]
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 185, in __getitem__
    raise KeyError('The cache has no package named %r' % key)
KeyError: "The cache has no package named 'xserver-xorg-video-ati'"



```

I think that this is a "thing". . .

Is it this?:
[http://osdir.com/ml/ubuntu-bugs/2012-12/msg20474.html](http://osdir.com/ml/ubuntu-bugs/2012-12/msg20474.html)

or this?:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1093466](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1093466)

---

### Post by blortuga on 2013-01-19
(. . . . I don't think I need to be changing the owner of ~/.config/ibus/bus to root. That just sounds silly)

---

