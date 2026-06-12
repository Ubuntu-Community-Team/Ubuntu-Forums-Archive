---
title: "[SOLVED] Another &amp;quot;Error authenticating some packages&amp;quot; thread"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by togo59 on 2008-11-05
I am trying to upgrade from 8.04 to 8.10 over the network using the update manager.

I get```
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

gdm-guest-session
human-theme
libgphoto2-2
libgphoto2-port0
libtotem-plparser12
python-software-properties
software-properties-gtk
totem
totem-common
totem-gstreamer
totem-mozilla
totem-plugins
transmission-common
transmission-gtk
```

I've done:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean

```

My /etc/apt/sources.list is:
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

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
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main

```

BTW: The last line was recently added, I am trying to install OO 3.0 as well. The upgrade to 8.10 didn't work before I added this source.

I have read other threads on this issue and not found a solution.

Before I uninstall the problem packages, e.g.: [FONT="Courier New"]gdm-guest-session, human-theme, libgphoto2-2[/FONT], .. etc (see above), I would like to know if that would be safe as they have been installed, I assume, as a side effect of other installations.

Anyway, I hope there's a simpler way..

Any help and/or advice would be appreciated.

---

### Post by togo59 on 2008-11-07
When is the right time to bump a post? :confused:

How about now?

---

### Post by wkulecz on 2008-11-07
I don't know, but if you've installed any NON AUTHENTICATED packages your system could now be hacked.

Automatic update servers would be the holy grail of hackdom if not for the packages being digitally signed and the verification keys served up seperately.  Obviously if both servers were hacked and the malware packaged also had its new key served up to authenticate it we'd be doomed.

But this would require near simultaneous hacking on the repository and key server as otherwise the corruped packages or keys would alert you things didn't match.  If you proceed through the warning, it could be game over unless it really is only a glicth in the authentication server and not a malicious attack.

Its why I'd be very worried about this!

--wally.

---

### Post by togo59 on 2008-11-07
> **wkulecz said:**
> 
Its why I'd be very worried about this!

I'm always worried, just ask my psychologist.

Wipe the partitions, throw the lap top in the bin and re-install the George 4 operating system? I've already torn up my credit card and passport.

Seriously, what do you advise? Clean install?

Ill-advised software, i.e. not installed via Synaptic, might include Unison (file synchronisation), Conduit (ditto, since Unison didn't work with my USB drive), and various programmatical stuff including Netbeans, eXist, Google's protocol buffer and an aborted attempt to install OO 3.0

---

### Post by wkulecz on 2008-11-07
If you are a single machine a complete reformat of the hard drive(s) and re-installation should be sufficient.  If you've a local network you have to worry about this machine now being a vector to infect the others.

There is a new Windows RPC worm which can't get through any decently configured firewall from the outside, but from the inside it has potential to rapidly infect local machines.  Using a Linux update to get thru the firewall to then exploit the local Windows machines would be a tempting target, as is Email based "social engineering" attacks.

I'm behind a major league firewall, supported by people who carry guns to prevent physical breach, but I really need to be careful about what I bring in via Linux, or Windows for that matter.  The Windows boxes are maintained by "experts" and *should* already be fully patched.

I'm swimming against the current using Linux and if I screw up network security it'll be game over for me.

--wally.

---

### Post by togo59 on 2008-11-07
I don't want to be complacent but isn't there a more benign reason why I get the authentication errors?

What symptoms should I watch for i.e. how can I tell whether I have malware on my laptop? Presumably the Windows worm is not transgenic?!! Ubuntu doesn't have a malware checker, AFAIK, and I don't want to install an unauthorized one!

There are always Windows attacks going on, which is half the reason I prefer Linux but obviously, nothing's safe these days.

---

### Post by wkulecz on 2008-11-07
> I don't want to be complacent but isn't there a more benign reason why I get the authentication errors?


I'd hope so.  Maybe something as simple as a network connectivity problem where you can get the package but not the authentication.

I'm having these errors on some 8.04 updates that accumlated while I was on vacation.  I am not doing the update until the issue is resolved!  Since its been almost 24 hrs since I first had the problem, I'm doubting its a network connectivity glitch.  Perhaps the updated digital signatures were forgotten to be done, hopefully word about this somehow gets back to the maintainers of the repositories so they can be fixed.

As to detecting, Google for:  chkrootkit, rkhunter, OSSEC

Generally you'll need to boot from a "live CD" and scan the hard drive in question.

HTH,
--wally.

---

### Post by togo59 on 2008-11-12
Just like to say that after trying several (about 10) times, leaving it for a week and then trying again, it finally worked. I didn't actually change anything in the mean time.

The upgrade went smoothly and 8.1 really rocks. I have an ATI graphics card and it's fine. Everything is fine. Fine, fine fine. :D

---

