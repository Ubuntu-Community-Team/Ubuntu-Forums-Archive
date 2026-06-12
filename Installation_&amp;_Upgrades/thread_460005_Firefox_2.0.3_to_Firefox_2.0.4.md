---
title: "Firefox 2.0.3 to Firefox 2.0.4"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by alligoodw on 2007-05-31
When upgrading software using Ubuntu, do I have to uninstall the older version before installing the newer?  Case in point . . .Firefox.  I've noticed that the update function (in Firefox) doesn't work under Ubuntu.

---

### Post by apunc1 on 2007-05-31
are you running the ubuntu build or the firefox build?

edit: how did you upgrade to firefox version 2 if you are running it
this works for me

> Update Official Mozilla Build of Firefox

If you already have the official build installed (e.g., by following the instructions above at some point before), you don't have to go through using the instructions in the previous section. You can use the built-in "Updates" functionality of Firefox.

In order for Firefox to update itself, it will have to be run as root. So quit all Firefox windows, and in a terminal, type:

gksudo firefox &

This will start Firefox as root. Select Help > Check for Updates from the menu, and it will find an update and download it. You will then get a message that says Firefox needs to be restarted to apply the update, and you can choose Later or Restart Firefox Now. Choose Restart Firefox Now. Firefox will restart again as root and tell you it's been updated. Now, you can close Firefox again, and then start it as normal from the menu, not as root. And you should be all good to go! 

---

### Post by mikewhatever on 2007-05-31
Do not worry. Firefox will be upgraded in a few days through synaptic.
Upgrading obviously means you have an older version installed, otherwise, what do you upgrade.

---

### Post by alligoodw on 2007-05-31
> **mikewhatever said:**
> Do not worry. Firefox will be upgraded in a few days through synaptic.
Upgrading obviously means you have an older version installed, otherwise, what do you upgrade.

Sorry guys!  I keep forgetting I'm not in Kansas anymore.  I keep forgetting about the auto update feature.

---

### Post by youspeakmylanguage on 2007-06-05
> **apunc1 said:**
> are you running the ubuntu build or the firefox build?

edit: how did you upgrade to firefox version 2 if you are running it
this works for me

Updating through sudo causes all of my settings and favorites to disapear/reset. Is there any way to keep this from happening?

Thanks,

---

### Post by apunc1 on 2007-06-06
> **youspeakmylanguage said:**
> Updating through sudo causes all of my settings and favorites to disapear/reset. Is there any way to keep this from happening?

Thanks,

yikes. i didn't have that problem. did you use the ubuntuzilla script to upgrade to firefox 2? if so, you could post your problem in the ubuntuzilla section of these forums [http://ubuntuforums.org/forumdisplay.php?f=251]("http://ubuntuforums.org/forumdisplay.php?f=251")
they are very helpful.

otherwise, i'm not sure what the problem is.good luck.

---

