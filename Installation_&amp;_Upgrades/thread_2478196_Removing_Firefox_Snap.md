---
title: "Removing Firefox Snap"
date: 2022-08-19
forum: Installation &amp; Upgrades
---

### Post by echotech2 on 2022-08-19
I updated from 20.04 to 22.04 from the Software Updater. Only one slight hiccup; In the middle of the install i got a popup "Front end not responding. - Wait/Force Quit". It sat there for about an hour while I had supper so I Force Quitted it and let it continue. Let the installer (Did I have a choice?) do its thing with Firefox.  Rebooted and tried out the "new" Firefox. No Bookmarks, Passwords, Addons, changes I made (e.g. Bookmarks Sidebar).

  Sorry Snap,you only get one strike in this game.  Installed Firefox from Mozillateam PPA and all is copacetic .

  Question1 is: snap remove  --purge will do what I want?

  Question2 is:  I read somewhere that I can't find now that I need to change something (in the repositories?) to keep Firefox Snap from loading in the future updates?  Any hints?

---

### Post by VMC on 2022-08-19
Here's what's replied on *askubuntu*:
```
sudo rm -rf /var/cache/snapd/
sudo apt autoremove --purge snapd gnome-software-plugin-snap
rm -fr ~/snap
sudo apt-mark hold snapd
```
For me just purging snapd has never brought it back.

---

### Post by echotech2 on 2022-08-19
Sorry, I wasn't clear about that. I only wanted to remove Firefox snap...  e.g.  snap remove --purge firefox  and mark Firefox so updates don't try to install Firefox snap.

---

### Post by &amp;KyT$0P# on 2022-08-19
After removing Firefox snap, you need to pin the Mozillateam PPA to a higher priority as explained [here]("https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/").

Make sure you understand apt pinning if you do this.  Refer to [FONT=Courier New]man apt_preferences[/FONT] for more info

* To get information useful to help you choose the pinning criteria, run
```
apt-cache policy
```

---

