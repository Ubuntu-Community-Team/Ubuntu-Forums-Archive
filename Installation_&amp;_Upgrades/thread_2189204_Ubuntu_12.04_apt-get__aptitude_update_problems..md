---
title: "Ubuntu 12.04 apt-get / aptitude update problems."
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by jim30 on 2013-11-21
Hi,

I have suddenly started having issues when running agt-get or aptitude update commands:

```

$ sudo apt-get update
Hit http://ppa.launchpad.net precise Release.gpg
...
Ign http://repo.steampowered.com precise/steam Translation-en
Reading package lists... Error!
E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

```

$ sudo aptitude update
E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Hit http://extras.ubuntu.com precise Release.gpg
...
Ign http://repo.steampowered.com precise/steam Translation-en
[ ERR] Reading package lists
E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

I've tried removing the Merge List as suggested [here]("http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err"):
```

sudo rm /var/lib/apt/lists/* -vf

```

But it doesn't appear to have any effect. I'm guessing there is a probelm with the xserver-xorg-input-vmmouse package but...

```

$ sudo apt-get remove xserver-xorg-input-vmmouse
Reading package lists... Error!
E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

Launching update manager or synaptic also errors:

Update Manager:

```

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Malformed 3rd word in the Status line, E:Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

```

Synaptic:

```

E: Malformed 3rd word in the Status line
E: Error occurred while processing xserver-xorg-input-vmmouse (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

Any help would be seriously appreciated...

---

### Post by jim30 on 2013-11-21
OK, managed to fix it. The first few lines of my /var/lib/dpkg/status file:

```

Package: xserver-xorg-input-vmmouse
Status: install ok anstalled
Priority: optional
Section: x11
Installed-Size: 114
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1:12.9.0-0ubuntu0.1
Provides: xorg-driver-input

```

Note the 'Status: install ok anstalled' line.

Corrected 'anstalled' to 'installed' and now all seems good, but I have no idea how a typo slipped in...

---

