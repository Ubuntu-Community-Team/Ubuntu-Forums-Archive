---
title: "Bug #859373 effects?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by duemir on 2011-10-14
I was affected by [Bug #859373]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/859373") during Upgrade from 11.04 to 11.10
It looks like all packages were installed except flash player. But cleaning was skipped because of this.
I rebooted system and everything seems to work fine.
I ran "sudo apt-get update && sudo apt-get upgrade" - missing flash player was installed.
Then I ran "sudo apt-get autoremove" to make some cleaning.
Apart from this is there anything that I should do to ensure consistency of the system?

---

