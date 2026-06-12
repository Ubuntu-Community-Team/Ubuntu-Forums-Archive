---
title: "Peril in sourcelist upgrade option"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by jlhughes on 2006-06-01
Instructions at wiki.ubuntu.com/DapperUpgrades say

Change every occurrence of "breezy" to "dapper" in sources.list and then: sudo apt-get update && sudo apt-get dist-upgrade

Unfortunately that creates problems if you have any breezy sources that are not available for Dapper. 

After downloading the files my installation failed, reporting that one of my repositories caused the problem.

BEING AN IGNORANT NEWBIE I thought the process was complete up to that point and rebooted the machine.

Needless to say, the system failed to boot the xserver.

sudo dpkg-reconfigure xserver-xorg told me the package was broken.

dpkg-reconfigure xserver-xorg reported missing dependencies and suggested apt-get -f install.

sudo apt-get -f install restarted the installation process.

After about a half-hour, the screen would return to the Xorg broken message and when I hit return to exit the Xorg error message the installation configuration continued.  This happened several times until I was finally dropped at the terminal prompt.

After power-cycling the box, Ubuntu started without error.   

;)

---

### Post by llamakc on 2006-06-01
So you fixed it? Cool.

---

