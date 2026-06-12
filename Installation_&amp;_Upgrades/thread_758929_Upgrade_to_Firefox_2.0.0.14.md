---
title: "Upgrade to Firefox 2.0.0.14"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by Daddyo-613 on 2008-04-18
I running Ubuntu Gutsy 7.10. I just upgraded Firefox to 2.0.0.14. 
The "Check for Upgrades" line on the "Help" pull down menu on the browser is in grey scale and doesn't activate.

How do I activate "Check for Updates" so I can do a manual check when I want to.

---

### Post by Pumalite on 2008-04-18
sudo apt-get update
sudo apt-get upgrade

---

### Post by Daddyo-613 on 2008-04-18
Thanks for the prompt reply. I may not have been clear in my posting. The issue is not how I can manually check for updates. I can do that using a terminal or the GUI Update Manager. What I am trying to figure out is how I can activate the "check for updates" line on the Firefox "help" pull down menu so that I can check for updates from the browser itself.

It just bugs me when features in a program are disabled and I don't know why.

---

### Post by Pumalite on 2008-04-18
[http://support.mozilla.com/en-US/kb/Upgrading+Firefox](http://support.mozilla.com/en-US/kb/Upgrading+Firefox)

---

### Post by confused57 on 2008-04-18
You also may want to check this out:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by mikewhatever on 2008-04-18
That feature is disabled because we get upgrades for FF from Ubuntu repositories and not from Mozilla. You are free to download and install FF manually from Mozilla. That version would not rely on the repositories and should have the feature you want enabled.

---

### Post by Pumalite on 2008-04-18
If you want to download the latest version from the site, place it on your Desktop. Then:
cd ~/Desktop
tar xvzf firefox-2.0.0.14.tar.gz
cd firefox
./firefox

Make sure firefox is closed when you do this

---

