---
title: "E: Could not perform immediate configuration on 'gir1.2-unity-4.0'"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by scottywz on 2011-12-05
I was trying to upgrade my netbook from Natty to Oneiric, and I got:

```
E: Could not perform immediate configuration on 'gir1.2-unity-4.0'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

This happened both when I tried upgrading through the update manager and when I tried it via `sudo do-release-upgrade`.

I tried installing gir1.2-unity-4.0 manually and I got:

```
$ sudo dpkg -i gir1.2-unity-4.0_4.0.6-0ubuntu3_i386.deb
dpkg: considering removing gir1.2-unity-3.0 in favour of gir1.2-unity-4.0 ...
dpkg: no, cannot proceed with removal of gir1.2-unity-3.0 (--auto-deconfigure will help):
 ubuntuone-client depends on gir1.2-unity-3.0 (>= 3.8.4)
  gir1.2-unity-3.0 is to be removed.
dpkg: regarding gir1.2-unity-4.0_4.0.6-0ubuntu3_i386.deb containing gir1.2-unity-4.0:
 gir1.2-unity-4.0 conflicts with gir1.2-unity-3.0
  gir1.2-unity-3.0 (version 3.8.4-0ubuntu1) is present and installed.
dpkg: error processing gir1.2-unity-4.0_4.0.6-0ubuntu3_i386.deb (--install):
 conflicting packages - not installing gir1.2-unity-4.0
Errors were encountered while processing:
 gir1.2-unity-4.0_4.0.6-0ubuntu3_i386.deb
```

As I was writing this, I decided to try:

```
$ apt-get download gir1.2-unity-4.0
$ apt-get download ubuntuone-client
$ sudo dpkg -i gir1.2-unity-4.0_4.0.6-0ubuntu3_i386.deb ubuntuone-client_2.0.0-0ubuntu2.2_all.deb
$ sudo dpkg -i gir1.2-unity-4.0_4.0.6-0ubuntu3_i386.deb
```

and then I was able to upgrade via `sudo apt-get dist-upgrade -f`.  (Be sure to select lightdm as your default display manager when it asks.  If you get an error, run `sudo dpkg --configure -a` to resume the upgrade.)

I hope this helps someone.

---

### Post by drevicko on 2012-05-07
Thanks for the post! It inspired me to try fix things with the apt-get mechanism and a bit of faith in it's ability to not screw things up ;). Immediately after the upgrade aborting (ie: without a restart and withoug dpkg --configure -a) I tried this:

```
>sudo apt-get install gir1.2-unity-4.0
```

It went through without any problems (the list of what it did is quite long, but I did notice it say "Removing gir1.2-unity-3.0 ..." without complaint.

After that, I did 

```
sudo do-release-upgrade
```

And it no longer complains about unity 3.0. The upgrade has gone through ok and the system seems to be stable. Fingers crossed!

---

