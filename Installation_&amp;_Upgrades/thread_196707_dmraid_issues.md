---
title: "dmraid issues"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by jewishj on 2006-06-14
I am trying to install dapper on a RAID 0 using the [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) and [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) howtos and every time dmraid fails to install (after doing the debootstrap).  This is what I get:

```

apt-get install dmraid
Reading package lists... Done
Building dependency tree... Done
dmraid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up dmraid (0.9.9+1.0.0.rc9-2ubuntu1) ...
 * Setting up DMRAID devices... invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: error processing dmraid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dmraid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The FakeRaid howto mentions that this may happen and says to use dpkg-reconfigure dmraid to fix it, but this just returns a similar error for me which says the package is broken.

Thanks

---

### Post by paradexes on 2006-06-18
I have the exact same problem. I am using an LSI megaraid i4. No raids are configured on my motherboard at all. Just on the IDE Raid card.

---

### Post by jewishj on 2006-06-19
I managed to fix this by just ignoring the error.  &#12288;I guess the problem was that it couldn't run because I wasn't running from the kernel in that root or something.. i dunno.

---

### Post by Ocxic on 2006-06-19
dmraid is depriciated use mdadm

---

