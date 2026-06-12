---
title: "1204 Hardware enabled stack end-of-life"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by edwardsah3 on 2014-07-20
I was just alerted that in about two weeks, certain packages in the 12.04 LTS will lose support, and that I have either to move to 14.04, or to install 14.04 HWE. When I run 

*hwe-support-status --verbose*

I get:

[I]Your current Hardware Enablement Stack (HWE) is going out of support
on 08/07/2014.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available.

For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)

To upgrade to a supported (or longer supported) configuration:

* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade 

OR

* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

and reboot your system.
[/I]
However, when I run 

*sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty*

I get:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx-lts-trusty : Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but it is not going to be installed
 xserver-xorg-lts-trusty : Recommends: xserver-xorg-input-all-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-video-all-lts-trusty but it is not going to be installed
                           Conflicts: libglapi-mesa:i386 (>= 0~)
E: Unable to correct problems, you have held broken packages.
[/I]
When I try to include libglapi-mesa-lts-trusty, I get a message:

 *libglapi-mesa-lts-trusty : Conflicts: libglapi-mesa:i386*

Finally, when I try 

*apt-get remove libglapi-mesa:i386 *

I get the message:

*Package libglapi-mesa:i386 is not installed, so not removed*

So, is it that the upgrade isn't actually ready?

Art Edwards

---

### Post by grahammechanical on 2014-07-20
If you look around this forum you will notice that others have received this update offer and accepted it and the result was a broken OS. Here are a couple of examples.

[http://ubuntuforums.org/showthread.php?t=2234830](http://ubuntuforums.org/showthread.php?t=2234830)

[http://ubuntuforums.org/showthread.php?t=2234815](http://ubuntuforums.org/showthread.php?t=2234815)

So, I would say that you are right. The upgrade is not ready. You should not think that Ubuntu 12.04 is no longer being supported. That continues into 2017. 

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

This will explain what an Hardware Enablement Stack is and why 12.04 is having the upgrade.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Is Ubuntu working fine on your hardware? Then ask yourself, Do In need this particular upgrade?

Regards.

---

