---
title: "Strange situation after upgrade 16.04 -&gt; 18.04 with Nvidia"
date: 2018-09-04
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2018-09-04
After using the Debian way [https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver]("https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver") to upgrade, I have some minor problems that I have already fixed.  However, I got the following Crash report:
```
Sorry, a problem occurred while installing software.
Package: Nvidia-kernel-common-390 390.48-0ubuntu3
```
The title in the report says:
```
package nvidia-kernel-common-390 390.480ubuntu3 failed to install/upgrade: trying to overwrite '/lib/udev/rules.d/71-nvidia.rules', which is also in package nvidia-384 384.130-0ubuntu0.16.04.1
```
There is other information, but if I check my NVIDIA X Server Settings, my driver version shows 390.48.  All the other settings seem fine.

If I check Synaptic, I see that all the libnvidia*390 packages are installed.  Synaptic also shows nvidia-367, nvidia-375, and nvidia-384 are installed as transitional packages.  If I try to install the supposedly failed install```
sudo apt install nvidia-kernel-common-390
``` I get```
nvidia-kernel-common-390 is already the newest version (390.48-0ubuntu3).
nvidia-kernel-common-390 set to manually installed.
```

Everything seems to be working fine.  Is it possible that when I took care of one of the errors shown on the install dialog that I corrected this crash?  Is there a way to tell if I need to make any adjustments?

BTW, I have been using Ubuntu since 8.04 and have always had massive problems with upgrades.  I finally started doing clean installs.  I decided to try the instructions in the above link to see if it worked better.  Voila!  It did.  This was one of the easiest upgrades I have ever done.  And I have a good number of PPA's as well as many additional programs installed.

---

