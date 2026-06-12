---
title: "Dependency Loop Preventing Distro Upgrade"
date: 2022-04-26
forum: Installation &amp; Upgrades
---

### Post by maxdunitz on 2022-04-26
[COLOR=#232629][FONT=-apple-system]I have found my system to be buggy, and I am trying to upgrade to Ubuntu 20.04 from Ubuntu 18.04. I tried running [FONT=courier new]do-release-upgrade[/FONT] after [FONT=courier new]full-upgrade[/FONT] and [FONT=courier new]dist-upgrade[/FONT] and got[/FONT][/COLOR]
```
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

```[COLOR=#232629][FONT=-apple-system]
The command [FONT=courier new]sudo apt-get update && sudo apt-get[/FONT] [FONT=courier new]upgrade[/FONT] gives[/FONT][/COLOR]
```
Fetched 88,7 kB in 3s (27,5 kB/s)                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```[COLOR=#232629][FONT=-apple-system] Then [FONT=courier new]apt list --upgradable[/FONT] gives[/FONT][/COLOR]
```
Listing... Done
libdrm-amdgpu1/focal 2.4.107-1029 amd64 [upgradable from: 2.4.101-2~18.04.1]
N: There are 27 additional versions. Please use the '-a' switch to see them.

```[COLOR=#232629][FONT=-apple-system]
I can't seem to upgrade this package. If I try to get rid of it with [FONT=courier new]sudo apt-get remove libdrm-amdgpu1 [/FONT]I get the following message:[FONT=courier new]
[/FONT][/FONT][/COLOR]
```
The following packages have unmet dependencies:
 x11-utils : Depends: libgl1-mesa-glx but it is not going to be installed or
                      libgl1 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```[COLOR=#232629][FONT=-apple-system][FONT=courier new]
[/FONT]which leads to a dependency loop. 
[FONT=Verdana]If I try ```
sudo apt-get remove --auto-remove libgl*
``` I get the following error:[/FONT]

[FONT=Verdana]```
The following packages have unmet dependencies:  x11-utils : Depends: libgl1-mesa-glx but it is not going to be installed or libgl1 but it is not going to be installed
```[/FONT]

[FONT=Verdana]But if I try [/FONT]```
[FONT=Verdana]sudo apt-get remove --auto-remove x11-utils[/FONT]
```
[FONT=Verdana]I get the opposite error:[/FONT][COLOR=#232629][FONT=Verdana][FONT=-apple-system]
[/FONT][/FONT][/COLOR]```
[FONT=Verdana]The following packages have unmet dependencies: libglx0:i386 : Depends: libglx-mesa0:i386 but it is not going to be installed[/FONT]
```[FONT=courier new]

[/FONT][FONT=Verdana]If I try instead to upgrade with[/FONT] [FONT=courier new]sudo apt-get upgrade libdrm-amdgpu1[/FONT] I get the message:[/FONT][/COLOR]
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libdrm-amdgpu1 : Depends: libc6 (>= 2.28) but 2.27-3ubuntu1.5 is to be installed
E: Broken packages


```[COLOR=#232629][FONT=-apple-system]I also saw some advice to run [FONT=courier new]apt list --installed | grep -v bionic[/FONT] which I think lists the software I installed that doesn't have a release for my current version of Ubuntu (Ubuntu 18.04.2 LTS (beaver-osp1-varys X34)). This produces the following list:[/FONT][/COLOR]
```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
Listing...
canonical-oem-keyring/now 2009.07.23+build3 all [installed,local]
cnijfilter2/now 6.30-1+1804 amd64 [installed,local]
davmail/now 6.0.1-3390-1 all [installed,local]
dell-recovery/now 1.61~somerville5 all [installed,local]
dell-recovery-casper/now 1.61~somerville5 all [installed,local]
dell-service-meta/unknown,unknown,now 7ubuntu3 all [installed]
dell-super-key/now 0.04 all [installed,local]
ferdi/now 5.5.0-2116 amd64 [installed,local]
franz/now 5.6.1-1830 amd64 [installed,local]
libdrm-common/focal,now 2.4.107-1029 all [installed]
libdrm-intel1/focal,now 2.4.107-1029 amd64 [installed,automatic]
libdrm-nouveau2/focal,now 2.4.107-1029 amd64 [installed,automatic]
libdrm-radeon1/focal,now 2.4.107-1029 amd64 [installed,automatic]
libdrm2/focal,now 2.4.107-1029 amd64 [installed]
libva-drm2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
libva-wayland2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
libva-x11-2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
libva2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
manage-distro-upgrade/now 2.1~18.04timbuktu1 all [installed,local]
manage-estar-settings/now 1.2~18.04timbuktu1somerville1 all [installed,local]
ocenaudio/now 3.10.3-1 amd64 [installed,local]
oem-beaver-osp1-varys-meta/now 1 all [installed,local]
oem-fix-eth-realtek-disabletlpr8153/unknown,unknown,now 2ubuntu8 all [installed]
oem-hotkey-osd/now 0.4~18.04timbuktu1 all [installed,local]
oem-release/now 1 all [installed,local]
oem-seventy-percent-brightness/now 1.5 all [installed,local]
oem-somerville-partner-archive-keyring/unknown,unknown,now 1.0.1 all [installed,automatic]
oem-ubuntu-boot-video/now 1 all [installed,local]
quarto/now 0.9.188 amd64 [installed,local]
scangearmp-common/now 2.30.1-1804+2ubuntu4 amd64 [installed,local]
scangearmp-mg6200series/now 2.30.1-1804+2ubuntu4 amd64 [installed,local]
```

[COLOR=#232629][FONT=-apple-system]I have a Dell Precision without a NVIDIA graphics card, just the on-chip Intel graphics. I attempted to install the software DaVinci Resolve, after which my computer started to randomly shut off and overheat. So I removed it but maybe have some GPU-related dependencies still installed? I was pretty agressive about uninstalling. (I also accidentally removed some packages like System Info, Settings, and so forth when trying to remove all traces of DaVinci Resolve...)[/FONT][/COLOR]

---

### Post by Impavidus on 2022-04-27
> **maxdunitz said:**
> [COLOR=#232629][FONT=-apple-system]I have found my system to be buggy, and I am trying to upgrade to Ubuntu 20.04 from Ubuntu 18.04.[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]Release-upgrading doesn't fix problems, but usually makes them worse. Except driver problems fixed with a more recent kernel.
[/FONT][/COLOR]> [COLOR=#232629][FONT=-apple-system]Then [FONT=courier new]apt list --upgradable[/FONT] gives[/FONT][/COLOR]
```
Listing... Done
libdrm-amdgpu1/focal 2.4.107-1029 amd64 [upgradable from: 2.4.101-2~18.04.1]
N: There are 27 additional versions. Please use the '-a' switch to see them.

```[COLOR=#232629][FONT=-apple-system]The current version of the package is the latest for Ubuntu 18.04, the version it proposes to upgrade too is a non-standard version. Somehow forcing this upgrade will make things worse.[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]

> I also saw some advice to run [FONT=courier new]apt list --installed | grep -v bionic[/FONT] which I think lists the software I installed that doesn't have a release for my current version of Ubuntu (Ubuntu 18.04.2 LTS (beaver-osp1-varys X34)). This produces the following list:```
[/FONT][/COLOR]WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
Listing...
canonical-oem-keyring/now 2009.07.23+build3 all [installed,local]
cnijfilter2/now 6.30-1+1804 amd64 [installed,local]
davmail/now 6.0.1-3390-1 all [installed,local]
dell-recovery/now 1.61~somerville5 all [installed,local]
dell-recovery-casper/now 1.61~somerville5 all [installed,local]
dell-service-meta/unknown,unknown,now 7ubuntu3 all [installed]
dell-super-key/now 0.04 all [installed,local]
ferdi/now 5.5.0-2116 amd64 [installed,local]
franz/now 5.6.1-1830 amd64 [installed,local]
libdrm-common/focal,now 2.4.107-1029 all [installed]
libdrm-intel1/focal,now 2.4.107-1029 amd64 [installed,automatic]
libdrm-nouveau2/focal,now 2.4.107-1029 amd64 [installed,automatic]
libdrm-radeon1/focal,now 2.4.107-1029 amd64 [installed,automatic]
libdrm2/focal,now 2.4.107-1029 amd64 [installed]
libva-drm2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
libva-wayland2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
libva-x11-2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
libva2/focal,now 2.13.0+i643~u20.04 amd64 [installed,automatic]
manage-distro-upgrade/now 2.1~18.04timbuktu1 all [installed,local]
manage-estar-settings/now 1.2~18.04timbuktu1somerville1 all [installed,local]
ocenaudio/now 3.10.3-1 amd64 [installed,local]
oem-beaver-osp1-varys-meta/now 1 all [installed,local]
oem-fix-eth-realtek-disabletlpr8153/unknown,unknown,now 2ubuntu8 all [installed]
oem-hotkey-osd/now 0.4~18.04timbuktu1 all [installed,local]
oem-release/now 1 all [installed,local]
oem-seventy-percent-brightness/now 1.5 all [installed,local]
oem-somerville-partner-archive-keyring/unknown,unknown,now 1.0.1 all [installed,automatic]
oem-ubuntu-boot-video/now 1 all [installed,local]
quarto/now 0.9.188 amd64 [installed,local]
scangearmp-common/now 2.30.1-1804+2ubuntu4 amd64 [installed,local]
scangearmp-mg6200series/now 2.30.1-1804+2ubuntu4 amd64 [installed,local]
```
That software from other sources must be the problem.

You could consider skipping 20.04 and jumping straight to 22.04 with a fresh install. Else, you'll have to remove those other repositories and remove the software coming from them, or downgrade to the versions from the official repositories. Which may not be so easy.

---

