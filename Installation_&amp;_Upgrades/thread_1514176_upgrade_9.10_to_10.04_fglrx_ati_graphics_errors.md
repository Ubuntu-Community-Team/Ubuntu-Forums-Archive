---
title: "upgrade 9.10 to 10.04 fglrx ati graphics errors"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by ledzepjes on 2010-06-20
I recently upgraded 9.10 to 10.04 and couldn't setup my ati 4850 properly. after reading lots of threads, and a bug related to my problem:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/565407](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/565407)
and:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
and:
[http://forums.debian.net/viewtopic.php?f=5&t=52486](http://forums.debian.net/viewtopic.php?f=5&t=52486)


I think I got it worked out.

Before, I was able to change my resolution to higher than 1024*768 in System-Preferences-Monitors, and it correctly displayed the model as a "Viewsonc", which was a plus. But I couldn't enable the proprietary ATI graphics drivers in System-Administration-Hardware Drivers or as a result, enable compiz effects. Bummer.

I tried to install fglrx in synaptic and using "& sudo apt-get install fglrx", but got errors similar to this:

[PHP]== DESCRIPTION ==
Installation of package fglrx failed with the following error:
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu2_i386.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati. This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for. Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is
not recommended).

dpkg: error processing
/var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1

The preinst script removes the /etc/ati directory _before_ running the ATI's uninstallation script. Hence the later complains about it not being there anymore.

TEST CASE:
1. install the drivers from ATI (download the installer e.g ati-driver-installer-10-3-x86.x86_64.run and run it )
2. install the package from the Ubuntu repository
   $ sudo apt-get install fglrx
The installation crashes with the aforementioned error.
3. purge fglrx
4. reinstall the drivers from ATI (step 1)
5. install fglrx from -proposed
6. Verify that it install correctly and the drivers from ATI are removed.

== WORKAROUND ==
$ export FORCE_ATI_UNINSTALL=/usr/share/ati
$ apt-get install fglrx

OR

- reinstall from the ATI installer to restore the /etc/ati directory
- then uninstall with ATI script
- finally installthe ubuntu package.

E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu2_i386.deb: subprocess new pre-installation script returned error exit status 1

When running update manager on a laptop after the 9.10 -> 10.04 upgrade.
Card is Radeon 2400

ProblemType: Package
DistroRelease: Ubuntu 10.04
Package: fglrx (not installed)
ProcVersionSignature: Ubuntu 2.6.31-21.59-generic
Uname: Linux 2.6.31-21-generic i686
NonfreeKernelModules: fglrx
AptOrdering:
 fglrx: Install
 fglrx: Configure
 fglrx-amdcccle: Configure
 fglrx-kernel-source: Configure
 xorg-driver-fglrx: Configure
Architecture: i386
Date: Sat Apr 17 17:04:09 2010
DkmsStatus:

ErrorMessage: subprocess new pre-installation script returned error exit status 1
MachineType: ASUSTeK Computer Inc. F8P
ProcCmdLine: root=UUID=6c566782-b53f-4a1d-b3f5-8cd82ee10bcb ro quiet splash
SourcePackage: fglrx-installer
Title: package fglrx (not installed) failed to install/upgrade: subprocess new pre-installation script returned error exit status 1
dmi.bios.date: 08/09/2007
dmi.bios.vendor: American Megatrends Inc.
dmi.bios.version: 201
dmi.board.asset.tag: ATN12345678901234567
dmi.board.name: F8P
dmi.board.vendor: ASUSTeK Computer Inc.
dmi.board.version: 1.0
dmi.chassis.asset.tag: ATN12345678901234567
dmi.chassis.type: 10
dmi.chassis.vendor: ASUSTeK Computer Inc.
dmi.chassis.version: 1.0
dmi.modalias: dmi:bvnAmericanMegatrendsInc.:bvr201:bd08/09/2007:svnASUSTeKComputerInc.:pnF8P:pvr1.0:rvnASUSTeKComputerInc.:rnF8P:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:
dmi.product.name: F8P
dmi.product.version: 1.0
dmi.sys.vendor: ASUSTeK Computer Inc.
system:
 distro: Ubuntu
 codename: lucid
 architecture: i686
 kernel: 2.6.31-21-generic[/PHP]

I was able to see that searching for "ati" in synaptic showed packages that I later uninstalled "xserver-xorg-video-ati" and also "xserver-xorg-video-radeon". I also opened as administrator and renamed the folder "/usr/share/ati" to "/usr/share/ati_old". Don't know if it needs to be opened as administrator to be renamed but I did it for good measure.



I rebooted and tried to install the proprietary ATI drivers a second time by opening System-Administration-Hardware Drivers and activating the ATI drivers. The second time worked. I checked in synaptic package manager and fglrx was indeed installed.

---

