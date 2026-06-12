---
title: "ERROR: Failed to retrieve status information from Google attempting to set up pepperf"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2016-04-03
I ran into a problem at one of the Alphabet servers attempting to install Adobe® Flash Player® for Google® Pepper&#8482; Application Plug-in Interface 21.0.0.197 via the Package pepperflashplugin-nonfree 1.7ubuntu1.  From the Terminal, sudo apt-get install pepperflashplugin-nonfree reports back as follows:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ttf-mscorefonts-installer ttf-dejavu
The following NEW packages will be installed:
  pepperflashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/11.1 kB of archives.
After this operation, 70.7 kB of additional disk space will be used.
Selecting previously unselected package pepperflashplugin-nonfree.
(Reading database ... 222643 files and directories currently installed.)
Preparing to unpack .../pepperflashplugin-nonfree_1.7ubuntu1_amd64.deb ...
Unpacking pepperflashplugin-nonfree (1.7ubuntu1) ...
Setting up pepperflashplugin-nonfree (1.7ubuntu1) ...
ERROR: failed to retrieve status information from google : W: Can't drop privileges for downloading as file './var/lib/apt/lists/partial/dl.google.com_linux_chrome_deb_dists_stable_InRelease' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
More information might be available at:
  http://wiki.debian.org/PepperFlashPlayer

```

I am treating this issue, encountered in Ubuntu® Development Release 16.03b2, as a duplicate of [Bug #1398145](https://bugs.launchpad.net/ubuntu/+source/pepperflashplugin-nonfree/+bug/1398145), filed 1 January 2014, as it involves the Google® DL server (the original Bug involved the Debian® People server) and therefore may require a complicated workaround.  Expected behavior is a successful download and install, consistent with the PPA Package pepflashplugin-installer 21.0.0.197~cr49.0.2623.110.1-0skunk0 from [skunk@launchpad.net](http://launchpad.net/~skunk).  Actual behavior is as noted in the Code box above.
---
```
ApportVersion: 2.20-0ubuntu3
Architecture: amd64
DRM.card0.HDMI.A.1:
 edid-base64:
 dpms: On
 modes:
 enabled: disabled
 status: disconnected
DRM.card0.VGA.1:
 edid-base64:
 dpms: On
 modes:
 enabled: disabled
 status: disconnected
Desktop-Session:
 'None'
 'None'
 'None'
DetectedPlugins:

DistroRelease: Ubuntu 16.04
EcryptfsInUse: Yes
Env:
 'None'
 'None'
InstallationDate: Installed on 2016-03-27 (3 days ago)
InstallationMedia: Ubuntu 16.04 LTS "Xenial Xerus" - Beta amd64 (20160323)
Load-Avg-1min: 0.82
Load-Processes-Running-Percent: 0.2%
MachineType: Gigabyte Technology Co., Ltd. GA-MA78GM-S2HP
Package: chromium-browser 49.0.2623.87-0ubuntu1.1232
PackageArchitecture: amd64
ProcEnviron:
 LANGUAGE=en_US
 TERM=xterm-256color
 PATH=(custom, no user)
 LANG=en_US.UTF-8
 SHELL=/bin/bash
ProcKernelCmdLine: BOOT_IMAGE=/vmlinuz-4.4.0-16-generic root=UUID=7e8f5247-d70e-4084-b1cd-6cf9227030ba ro debug
ProcVersionSignature: Ubuntu 4.4.0-16.32-generic 4.4.6
Tags: xenial
Uname: Linux 4.4.0-16-generic x86_64
UpgradeStatus: No upgrade log present (probably fresh install)
UserGroups:

_MarkForUpload: True
dmi.bios.date: 12/16/2008
dmi.bios.vendor: Award Software International, Inc.
dmi.bios.version: F3
dmi.board.name: GA-MA78GM-S2HP
dmi.board.vendor: Gigabyte Technology Co., Ltd.
dmi.chassis.type: 3
dmi.chassis.vendor: Gigabyte Technology Co., Ltd.
dmi.modalias: dmi:bvnAwardSoftwareInternational,Inc.:bvrF3:bd12/16/2008:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA78GM-S2HP:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA78GM-S2HP:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:
dmi.product.name: GA-MA78GM-S2HP
dmi.sys.vendor: Gigabyte Technology Co., Ltd.

```

---

### Post by bcschmerker on 2016-04-18
**Update:**  pepperflashplugin-nonfree 1.8.2ubuntu1 fixes the issue.

---

