---
title: "Error Checking for Updates"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by geeky-1 on 2018-11-09
I just did a fresh install of Ubuntu 18.04 LTS and when I checked for updates, I get the message "Unable to download updates from "extensions.gnome.org": [*/*/*/source/shell-extensions/*] failed to download [https://extensions.gnome.org//static/extensions.json:](https://extensions.gnome.org//static/extensions.json:) Cannot resolve hostname"

---

### Post by QIII on 2018-11-09
Hello!

Had you added some GNOME extension that may not have a version for 18.04? 

You are getting that message for exactly the reason it sounds like.  When the link is clicked, all your get is a 404 - Not Found error.  That resource simply does not exist.

---

