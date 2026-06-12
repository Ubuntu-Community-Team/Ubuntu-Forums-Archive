---
title: "automated installation blows up looking for non-existant packages"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by netllama on 2006-03-09
I've been Googling on this, and have come up dry, so hopefully some of the experts here will be able to help.

I'm developing an automated install CD which uses kickstart to install breezy(5.10) for both x86 & x86_64 systems with the default "desktop" profile (i'm not adding in or removing any packages).  

I'll start off by saying that if I install from the 'official' x86 or x86_64 CDs, all is well.  My problem seems to be isolated to the kickstart installation that i'm doing.

I've copied the full content of each CD to a web (apache) server, and created a kickstart file that points to the location of the CD contents.  All of the inintial installation process seems to go well up through where the system reboots into the ubuntu kernel to complete the installation.  After that reboot is where everything goes south in the same exact fashion for both x86 and x86_64 installations.

In the installer screen I see:
There was a problem installing the selected software.  One or more packages failed to install.

In the base-config-pkgsel.log I see:
########
Preconfiguring packages ...
Fetched 46.9kB in 0s (3540kB/s)
Selecting previously deselected package popularity-contest.
(Reading database ... 11380 files and directories currently installed.)
Unpacking popularity-contest (from .../popularity-contest_1.30ubuntu1_all.deb) ...
Setting up popularity-contest (1.30ubuntu1) ...

^MReading package lists... 0%^M^MReading package lists... 0%^M^MReading package list
s... 55%^M^MReading package lists... Done
^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 0%^M^MBuilding depen
dency tree... 50%^M^MBuilding dependency tree... 50%^M^MBuilding dependency tree... 
Done
^MInitializing package states... 0%^M^MInitializing package states... 0%^M^MInitiali
zing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  kpdf: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  ksvg: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  ksnapshot: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  kooka: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  kdelibs4c2: Depends: libarts1c2 (>= 1.3.2) which is a virtual package.
              Depends: libopenexr2c2 (>= 1.2.2) which is a virtual package.
              Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  libxine1c2: Depends: libmodplug0c2 (>= 1:0.7-4.1) which is a virtual package.
  krita: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  koffice-libs: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  kdegraphics-kfile-plugins: Depends: libopenexr2c2 (>= 1.2.2) which is a virtual pa
ckage.
                             Depends: libqt3-mt (>= 3:3.3.4) which is a virtual pack
age.
  kghostview: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  kdelibs-bin: Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
               Depends: menu-xdg which is a virtual package.
#########

I'm completely puzzled about this, because I never explicitly requested any of those packages.  Does anyone know what I might be doing wrong?  Thanks!

---

