---
title: "How can I reinstall the latest upgrades?"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by peterdm on 2008-11-18
How can I find out what the most recently installed (today) packages are on my system and reinstall them again?

I case you're wondering why I want to do this, the reason is this: 

Today I was installing 14 upgrades when my desktop locked up.
The installation wasn't finished, but when after waiting a couple of minutes I pressed CTRL-ALT-BACKSPACE to restart X.
When I logged in after the restart, my desktop looked all ugly and the gnome theme was gone.
I suspect it is because the upgrade was only half finished, even though upgrade manager doesn't prompt me for those upgrades.
What I want to do now is to reinstall those upgraded packages.
However, I don't know what upgrades they were...

I already got firefox to work by reinstalling firefox-3.0 (I know for sure it was in the list of upgrades), so I have good hope the rest of the problems can be fixed in the same way.

Peter

---

### Post by Pumalite on 2008-11-18
Get into Recovery Mode and do this:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

