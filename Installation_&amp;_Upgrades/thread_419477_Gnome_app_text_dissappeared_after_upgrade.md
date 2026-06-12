---
title: "Gnome app text dissappeared after upgrade"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Burko on 2007-04-23
I just decided to upgrade today, but during upgrading, my laptop went into some kind of standby mode from which it didn't recover properly.

When I came back and completed the installation, all Gnome dialogs I saw, and programs such as Synaptic had squares in place of text, as though there were letters but the fonts weren't installed properly.

Is there some kind of font package I can reinstall to try and rectify the situation?

---

### Post by house7 on 2007-04-23
[http://ubuntuforums.org/showthread.php?t=416510](http://ubuntuforums.org/showthread.php?t=416510)

try manual installation... :)

[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

---

### Post by MrMacHead on 2007-04-24
I ended up with the missing system font problem as well, after some glitch occured in my Feisty upgrade. This is the fix that worked for me, thanks to a thread on this forum...

sudo apt-get dist-upgrade

---

