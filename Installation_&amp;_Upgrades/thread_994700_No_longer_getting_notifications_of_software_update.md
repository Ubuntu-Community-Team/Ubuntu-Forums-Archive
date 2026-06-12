---
title: "No longer getting notifications of software updates"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by biodiesel-bri on 2008-11-27
I upgraded from 8.04 to 8.10 a few weeks ago and things seem fairly smooth.  However, I'm not getting notified of software updates.

KDE used to have a nice systray applet and presumably a daemon that no longer seems to work.

Any ideas?  Adept-notifier seems deprecated, update-notifier-kde doesn't do anything when I run it from konsole, there are no plasmoids - I'm stumped.

Thanks!

---

### Post by automaton26 on 2008-11-27
I had a fresh install of Intrepid and now I've lost mine too, even though the correct options are ticked in the *Software Sources* dialog.

Now I have to manually:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

I'm not sure whether it's something I've done - I disabled a few services (like anacron) by using sysv-rc-conf, and messed around with the Widgets/Panel Settings.

Does anyone have any idea exactly which packages/services need to be installed and running for the taskbar notifications to work properly?

---

### Post by biodiesel-bri on 2008-12-01
ping [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

