---
title: "Cannot Upgrade to 20.04 - Keeps telling me to update"
date: 2020-08-22
forum: Installation &amp; Upgrades
---

### Post by deck on 2020-08-22
I am trying to upgrade from 18.04 to 20.04.  When I run Software Updater, I get the choice to do it, click on the button, the window disappears and nothing happens.

When I run "do-release-upgrade" or "apt-get dist-upgrade", I get a message to update my software.

Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

When  I run "apt-get upgrade" I get the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  wine-stable wine-stable-amd64 wine-stable-i386:i386 winehq-stable
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Apt-mark does not show Wine on hold.

When I try to do a manual install of the latest version of Wine (5.0.2), I get a huge dump of issues and the install fails .  I tried a manual remove of Wine and get another huge dump of issues and the remove fails.

I don't know what is going on.  Is there anyway to force a release upgrade?

deck

---

### Post by ubfan1 on 2020-08-23
Did you eer do the apt-get update before the apt-get dist-upgrade?

---

### Post by mrdc76 on 2020-08-23
Purging all PPAs might help. The crap that they install might cause problems like this for release upgrades.

---

### Post by CelticWarrior on 2020-08-23
Please try
```
sudo apt update && sudo apt full-upgrade
```
before trying again the release upgrade.


> [COLOR=#000000]Purging all PPAs might help[/COLOR]
Yes, PPAs can be a problem for release upgrades, namely the often unneeded Wine PPA that is at the core of your help packages issue. But purging will uninstall everything that has been installed from the purged PPA. Usually there's no need for this as disabling the PPAs should be enough.

---

