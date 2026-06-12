---
title: "Remove downloaded upgrade files *before* install"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by holiday on 2013-03-27
In 10.04, I mistakenly clicked Upgrade. The upgrade downloaded the upgrade info and then went on to the upgrade dialog telling me that it would download and install the upgrade. I cancelled the dialog, but the package manager will be expecting a go command at some point. 

I really really do not want to upgrade, in fact on my other computers I've switched to CrunchBang.

What can I do to remove the downloaded files, and reset the package manager so that it is not expecting to install the upgrade.

Thanks

---

### Post by schragge on 2013-03-27
Removing the downloaded files is easy: ```
sudo apt-get clean
``` As to the rest of your post, I don't quite understand it. What package manager are you using? aptitude? synaptic? I guess in synaptic it's a matter of filtering on packages marked for upgrade and unmarking them. IIRC, pressing **Ctrl**+**n** will also do it. In aptitude, **Ctrl**+**u** will undo the last action. You also can ```
sudo aptitude keep-all
```

Or you started an upgrade to a newer Ubuntu release in update-manager? Where have you canceled it? On the following screen?
[IMG]http://www.ubuntu.com/static/u/img/download/desktop-update-3-20.10.png[/IMG]

---

