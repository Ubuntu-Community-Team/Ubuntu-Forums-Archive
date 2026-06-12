---
title: "ZFS-on-root in alternate Ubuntu distros"
date: 2021-08-30
forum: Installation &amp; Upgrades
---

### Post by paulmauddib on 2021-08-30
I would like to do a lubuntu install, but with zfs-on-root.

ZFS-on-root is currently not an option available in the installer for most of the alternative flavors of Ubuntu.  In particular I'm looking at the Lubuntu distro but this is probably the case for others as well.

You can install mainline Ubuntu and then the desktop environment of your choice, but the lubuntu-desktop metapackage (for example) does not include the same package set and customization that is in the actual lubuntu distro itself when doing an install from Lubuntu media (eg all the bluetooth stuff is missing for example, and I'm sure there's more).

The other way I'm looking at doing it is to do a lubuntu install on disk A, do a zfs-on-root ubuntu install on disk B, then mount the zfs volumes and rsync them across.  Is that the easiest way to get a true lubuntu install at this point?

---

### Post by MAFoElffen on 2021-08-30
The easiest and fastest way, would to be to install fresh with Ubuntu Desktop 20.04.3 with ZFS and as a minimal install... Then covert it to server, which will remove all the ubuntu-desktop related packages, safely, with the correct, resolved dependency tree. Then install the package lubuntu-desktop... Like this:
```

sudo apt update
sudo apt install ubuntu-server
sudo apt autoremove
sudo apt install lubuntu-desktop

```
If you try to do it by uninstalling and purging ubuntu-desktop, it uninstalls just that package, and will leave dependencies orphaned and unresolved... Just saying...

---

### Post by guiverc on 2021-08-30
The only *file-systems* that are QA-tested with Lubuntu are

- default (ext4)
- luks encryption
- XFS
- BTRFS

For a number of releases I've also QA-tested installs with *reiser*fs (*but that's really so I can find the partition easier the next time on crowded disks with many installs*)

You didn't provide release details; modern Lubuntu uses `calamares` for its installer (releases up to 18.04 used `ubiquity` (*used by main Ubuntu & desktop flavors*) & the *debian installer* as the alternate installer) as the Qt skin for `ubiquity` was hard-coded to say Kubuntu/KDE (why Lubuntu & Ubuntu-Studio with it's Qt5 releases use `calamares`).

I can't imagine you ending up with a different set of package if you added `lubuntu-desktop` to a Ubuntu system though (*I've not noted any*).  Again you didn't provide release details so I cannot look, but you can for example see what's in a Lubuntu install (eg. *hirsute* [https://cdimage.ubuntu.com/lubuntu/releases/21.04/release/lubuntu-21.04-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/releases/21.04/release/lubuntu-21.04-desktop-amd64.manifest)) which I'd compare & give reasons possibly, but you gave no specifics on what your (*bluetooth missing*) differences were based on.

---

