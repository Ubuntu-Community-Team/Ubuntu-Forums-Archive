---
title: "Kernel panic when installing ubuntu 13.04"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by yichentohjoel on 2013-07-12
i have decided to install ubuntu 13.04, 64 bit version on my laptop which has windows 8 (upgraded form windows 7) unfortunately after selecting install alongside windows 8, my computer kernel panics and restarts itself. any help would be appreciated. (this is my first time posting on this forum)

---

### Post by buzzingrobot on 2013-07-12
Some folks, including me, have had that happen with the default kernel installed in 13.04.  If you can get the thing to boot correctly, apply the updates, either via the software updater gui tool, or via "sudo apt-get update  && sudo apt-get dist-upgrade" in a terminal.  That installed a newer kernel here, plus many other updates, and the system was then stable.

---

### Post by yichentohjoel on 2013-07-12
I tried installing it about several times already without much luck. is  there a older version of ubuntu that uses a different kernel? if so can i  use that and then upgrade the version and kernel form there?

---

### Post by buzzingrobot on 2013-07-13
You don't need to reinstall to give the kernel another chance at working. Just reboot.

Yes, 12.10 is the previous release, and 12.04 was the release before that.  They are still available. Both use different kernels. All use Unity as the default desktop.

The 12.04 release is a Long-Term-Service (LTS) release which is supported for 5 years.  13.04, on the other hand, is only suported for 9 months. What this means is that, after 9 months, security and bug fixes and updates will not be released for 13.04.  

You can install 12.10 and upgrade to 13.04. 

However, I'd suggest seriously considering installing the 12.04 LTS version and not upgrading. It's proven to be a very stable and satisfying release. The current version is "12.04.02"

Here's the page listing links to the releases:  [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

