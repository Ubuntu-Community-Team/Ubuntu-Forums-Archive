---
title: "Kcontrol empty after Gusty Upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by DaveTheAve on 2007-10-19
Situation:
When I upgraded to Gusty my Kcontrol was working; however, about two days ago after a gusty update, my KInfoCenter AND Kcontrol are empty. Well... almost, Kcontrol shows ONE empty folder labeled "Network". There are however, numerous files in the "Lost + Found" menu in kicker... all of which look like they belong to Kcontrol.

Question:
How do I restore functionality?

---

### Post by DaveTheAve on 2007-10-21
This isn't something I can just let go guys, I need my Kcontrol.

---

### Post by crypto2600 on 2007-10-23
Similar problem. Except the left panel for Kcontrol is completely blank in my case.
The "main" window shows the computer information as above.

System Settings works. 
Still need Kcontrol however.

I have trying "reinstalling" kcontrol through synaptic.
When I try to remove fully, it tries to remove the following:

kcontrol kde-core kde-extras kde-systemsettings kdeaddons kdebase kdebase-dev kmplayer-konq-plugins konq-plugins konqueror
  konqueror-nsplugins kubuntu-desktop kubuntu-konqueror-shortcuts smb4k strigi-applet

So I'm going to err on the side of caution and not do a full uninstall then reinstall

---

### Post by DaveTheAve on 2007-10-27
Come on poeple PLEASE help the both of us out. It has been a week now without an answer!!!!

---

### Post by DaveTheAve on 2007-10-27
Apparently their are many more people with this issue: [https://bugs.launchpad.net/ubuntu/+bug/152325](https://bugs.launchpad.net/ubuntu/+bug/152325)... but that isn't for my version... help please.

---

### Post by DaveTheAve on 2007-10-27
Forget it, I found a fix for myself....

> 
sudo rm /etc/xdg/menus/kde-applications-merged/kde-essential.menu


Than I reinstalled via ADEPT: kdebase, kdebase-bin, and kdebase-data.... then ADEPT crashed and I did a:

> sudo dpkg --configure -a

and when it asked if I wanted to replace the /etc/xdg/menus/kde-applications-merged/kde-essential.menu file I typed Y (yes).

---

### Post by Haiyadragon on 2008-01-29
I still have this problem. DaveTheAve's fix didn't work for me.

The kde-essential.menu isn't restored by apt. This seems like a pretty serious bug. Can anyone help me with this?

---

