---
title: "Upgrade issues from 15.10 to 16.04 LTS"
date: 2017-09-30
forum: Installation &amp; Upgrades
---

### Post by allensdunn on 2017-09-30
A bit of a backstory, I originally installed 15.10 couple of years ago on a laptop and created a partition specifically for Ubuntu. A few months after install, I let the computer gather dust and go into general disuse. However, I am actively trying to revive my use of the computer and trying to update things to current editions as best I can. 

My primary goal on this computer is to upgrade Ubuntu to 16.04 LTS. I have followed the steps that the main Ubuntu site recommends, but for some reason, the "Software & Updates" section in System Settings is not detecting the presence of any new versions, despite me setting it up so it should detect them. Any recommendations on how to proceed? I have no problem wiping the partition and starting from scratch if that's what it takes, although admittedly I'm not sure how to do it.

---

### Post by DuckHook on 2017-09-30
Welcome to the forums, allensdunn.

You won't be able to do a network upgrade at this point without setting *apt* to the archive repositories. I'm afraid 15.10 is too old to have any remnant presence in the main repos.

You seem to have little invested in the old install and are prepared to make a pristine install. This is probably the best way. There's not anything special that you must do. No need to wipe any partition, unless you wish to specially customize your install this time. If you simply want to install a standard 16.04 on the laptop, then just invoke the installation routine from the LiveUSB, follow instructions, answer the questions, and the installation media should handle your partitioning for you.

---

### Post by jeffroaltiere1 on 2017-09-30
Have you tried using ```
sudo apt-get upgrade
``` instead of ```
sudo apt-get update
```? Generally, I've noticed that the former brings up more updates, and can prompt the presence of a new Distro Update too. I'd be careful in this case, as it may bring up 17.04 instead of the LTS that you're looking for.

---

