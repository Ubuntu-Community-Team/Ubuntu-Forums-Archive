---
title: "Upgrade 9.10 -&gt; 10.04 didn't finish... now I have a Karmic Lynx!!"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by ghaspias on 2010-07-03
I have used ubuntu since Warty, and did a lot of upgrades (9.04 was my second install 'from scratch', because of a failed disk). Most of the times, upgrades went ok, but now I was a bit unsecure... after delaying upgrade for weeks, I finally decided to risk upgrading from my 9.10 to 10.04. This is what happened (I always keep notes in tomboy of anything unusual during updates and upgrades)

> During dist-upgrade, got the message:
Could not install '/var/cache/apt/archives/kvm-pxe_5.4.4-1ubuntu1.1_all.deb'
The upgrade will continue but the '/var/cache/apt/archives/kvm-pxe_5.4.4-1ubuntu1.1_all.deb' package may not be in a working state. Please consider submitting a bug report about it. unable to install new version of `/usr/share/kvm/pxe-e1000.bin': No such file or directory
-----
while setting up package kvm-pxe, got the message:
package kvm-pxe is already installed and configured
-----
[B]The final message from dist-upgrade was:
Could not install the upgrades

The upgrade is now aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).[/B]
-----
Didn't prompt for restart at the end.


After reboot, the result is that I feel it didn't finish the upgrade. Altough it seems functional, there are missing icons, the wallpaper dissapeared, the theme is a mix of old and new... 
I ran dpkg --configure -a, but it did nothing (in fact, all packages where configured).

Does anyone know how I can get it to re-run the missing steps from the upgrade? All packages seem to have been installed and configured properly,but usually there are some tweaks applied when upgrading, after the package configuration.
I guess if I get hold of the scripts that do the upgrade, I could run the needed last steps manually...

Thanks

---

