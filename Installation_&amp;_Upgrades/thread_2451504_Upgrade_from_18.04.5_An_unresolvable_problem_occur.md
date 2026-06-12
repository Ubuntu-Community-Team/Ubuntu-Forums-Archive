---
title: "Upgrade from 18.04.5: An unresolvable problem occurred while calculating the upgrade"
date: 2020-10-05
forum: Installation &amp; Upgrades
---

### Post by matej-kovacic on 2020-10-05
Tried to do upgrade from 18.04.5 to 20.04.

I have removed ALL PPA's from my system, run sudo do-release-upgrade and it still says:


 An unresolvable problem occurred while calculating the upgrade.

 If none of this applies, then please report this bug using the
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If
you want to investigate this yourself the log files in
'/var/log/dist-upgrade' will contain details about the upgrade.
Specifically, look at 'main.log' and 'apt.log'.


 
I took a look to:
/var/log/dist-upgrade/apt.log

 ...and quite a lot of stuff is broken. No idea why.

 
Any idea how to solve this?

Yes, I have some non-Ubuntu software installed. MS Teams, Google Chrome, VirtualBox, etc. But I removed all PPA's (but not the software itself). And upgrade is still not possible.

---

### Post by matej-kovacic on 2020-10-05
It seems you have to remove all "broken" packages:

grep Broken /var/log/dist-upgrade/apt.log

... which in my case means 411 packages! Including libreoffice-writer, gnome-settings-daemon-common, etc.

---

