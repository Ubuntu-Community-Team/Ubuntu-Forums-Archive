---
title: "Setting Server Upgrade Preferences"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by hbj on 2012-11-07
I am running Ubuntu 12.04.1 LTS server.  I want to set the preferences so that it only tells me about new LTS versions.  However, when I log in I get the message:

New release '12.10' available.
Run 'do-release-upgrade' to upgrade to it.

On a desktop system I would normally go into the package manager GUI to change the preference.  How can I do this on the server?  I'm comfortable with command-line work, just don't know where to look...

---

### Post by snowpine on 2012-11-07
> edit /etc/update-manager/release-upgrades and set Prompt=lts

source: [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by hbj on 2012-11-07
Perfect - thanks!

---

