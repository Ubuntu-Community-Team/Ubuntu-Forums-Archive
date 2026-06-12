---
title: "Upgrading to a newer e2fsprogs with an older Ubuntu version"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by david121 on 2013-12-04
[SIZE=3][FONT=arial]Recently I encountered an issue with a local data storage server where increasing the size of a LVM logical volume beyond 16TB (to 32TB) was possible, but expanding the ext4 filesystem to match it resulted in a resize2fs error.  It appears that this error has been fixed in more recent versions of e2fsprogs, so I would like to update my e2fsprogs.

The server is currently running Ubuntu 12.04 LTS (Precise Pangolin).
The version of e2fsprogs used in this release is [COLOR=#333333]1.42-1ubuntu2.
[/COLOR]
Ubuntu 13.10 (Saucy Salamander) uses e2fsprogs [COLOR=#333333]1.42.8-1ubuntu1, which appears to support expanding ext4 beyond 16TB with resize2fs.  I assume that this version is stable enough for common use but not as well tested.

My question is: Is possible to install the latest somewhat stable e2fsprogs (1.42.8-1ubuntu1) without upgrading my entire server installation from Ubuntu 12.04 LTS to 13.10 and without causing incompatibilities?  If so, how can I accomplish this?


Simply asking apt-get to install suggests that [/COLOR][/FONT][/SIZE][FONT=arial]e2fsprogs [/FONT][COLOR=#333333][FONT=arial]1.42.8-1ubuntu1[/FONT][/COLOR][SIZE=3][FONT=arial][COLOR=#333333] is the latest that is supported in the release I am using, as no new version is installed:
[/COLOR][/FONT][/SIZE]> sudo apt-get install e2fsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e2fsprogs is already the newest version.

[SIZE=3][FONT=arial]

Thanks in advance for any suggestions you may have.


[/FONT][/SIZE]

---

### Post by mikewhatever on 2013-12-04
Consider filing a bug report on launchpad.net. If the new version fixes a serious bug, it will get updated according to the [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates"). In case you can't spare a few minutes, get the source and build it.

---

### Post by david121 on 2013-12-04
Done: [https://bugs.launchpad.net/bugs/1257968](https://bugs.launchpad.net/bugs/1257968)
Thanks for the suggestion, mikewhatever - I didn't know about backports or filing bug reports for this purpose until you mentioned this.

---

