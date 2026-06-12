---
title: "trying to do a late upgrade from 14.04 to 16.04"
date: 2020-04-27
forum: Installation &amp; Upgrades
---

### Post by Hareyama Kosen on 2020-04-27
I have been slack in updating and the Software & Updates no longer offers an update beyond my last update to 14.04.
I have tried a number of the suggestions on the Forum but they are all years old and I think assume that 16.04 is the latest update. I have tried various approaches but have gotten nowhere. It seems that at this stage, there is no easy way to update from 14.04 to any of the newer releases.
Any suggestions?

---

### Post by howefield on 2020-04-27
Coming from so far back, I'd suggest a fresh install after backing up your important data, if this isn't possible then you could start here.. [https://ubuntu.com/tutorials/tutorial-upgrading-ubuntu-desktop#1-before-you-start](https://ubuntu.com/tutorials/tutorial-upgrading-ubuntu-desktop#1-before-you-start)

---

### Post by webaake on 2020-04-27
You could go a hazardous route to 18.04. It can be done and not all of us look forward to 20.04 (yet).
* Backup all your data
* Uninstall ALL unessecary apps. (and some more)
* Disable all third party repos
* Edit /etc/apt/sources.list and replace 'trusty' with 'bionic'
* Run the commands apt-get update and then apt-get upgrade
* Study the terminal closely and see what happens. There will be hickups - but they can be overcome.

Instead of apt-get, or just apt, I recommend the app aptitude. I've found it a little bit better of handling problems by suggesting solutions in a clear way.
This route is not recommended, but interesting and educational.

---

### Post by Impavidus on 2020-04-27
See here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But that's not recommended. Probably best to clean install and skip one or two LTS releases. That will be much faster and more reliable. Much has changed, so your old configurations no longer apply.

---

