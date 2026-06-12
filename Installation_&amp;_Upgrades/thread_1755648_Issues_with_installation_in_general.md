---
title: "Issues with installation in general"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by Ubuntization on 2011-05-11
Hi guys

I'm having problems with installation in general. It all started with trying to upgrade Totem to 3.0.1. I uninstalled the older version and tried to install the new one but it didn't work. Then Ubuntu software center stopped working completely which leaves me to use synaptics for installations. Then I tried reinstalling the old version of Totem cause it's the only media player that works for me for on-line streaming but when I try reinstalling it from Synaptics I get the following error message: 

totem:
 Depends: totem-plugins but it is not going to be installed
  Depends: totem-common (<2.29) but 3.0.0-0ubuntu1~build2 is to be installed
 Recommends: totem-mozilla but it is not going to be installed

Help me OB1 you are my only hope

PS: I'm running Karmic

---

### Post by mikewhatever on 2011-05-11
I suspect the problem is one of the two (or perhaps both):
1. You've not removed Totem 3.0.1 and all its dependencies.
Try 'sudo apt-get --autoremove purge' after removing Totem 3.
2. Karmic has reached EOL (End of Life) in April, so that the repositories are no longer available. It's time to move on.

---

