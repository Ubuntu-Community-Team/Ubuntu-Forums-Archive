---
title: "why is the updater broken?"
date: 2017-11-25
forum: Installation &amp; Upgrades
---

### Post by yonnie on 2017-11-25
lsb_release -a shows I'm running 16.04 LTS.  Package manager says I'm up to date.  Firefox says I'm using an old browser and need to update.  All the "old" usual cli stuff doesn't seem to work.  I know there are newer LTS versions available but why won't the usual methods work anymore.  I don't want to have to wipe the disk and reload everything just to get an update!  
Why should a 10 minute update/upgrade be an "all weekend" nightmare?

---

### Post by deadflowr on 2017-11-25
Hmm, yes why is the updater broken?
Please open a terminal and run
```
sudo apt-get update
```
and post back the results.

Also, there are no LTS versions newer than 16.04.
There are newer Ubuntu standard non-LTS versions available, but no new LTS versions.

---

### Post by photonxp on 2017-11-26
"Yard by yard it's hard; but inch by inch it's a cinch" -- old saying

Welcome to the club of mad linuxers, strugging to learn how to use a line of command to save a day of life:
> apt-get -s dist-upgrade | grep "^Inst"
This command simulates the installation of packages without actually installing any package. So it can be used safely without sudo.


Some more tips:

Firefox is in the repository of xenial-updates. 
> apt search firefox | grep "^firefox/"
Also check "System Settings" / "Software & updates" / "Updates"
See if (**xenial-updates**) is ticked too.

---

### Post by oldos2er on 2017-11-26
> **yonnie said:**
> lsb_release -a shows I'm running 16.04 LTS.  Package manager says I'm up to date.  Firefox says I'm using an old browser and need to update.  All the "old" usual cli stuff doesn't seem to work.  I know there are newer LTS versions available

16.04 is the latest LTS; 18.04 won't be released until next April.

Which version of firefox are you using?

---

