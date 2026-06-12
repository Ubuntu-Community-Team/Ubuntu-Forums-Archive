---
title: "Installing Codec"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by shellymoxley on 2008-04-12
how do you install codecs for mozilla firefox to play videos?

---

### Post by ajgreeny on 2008-04-12
Do a search for win32codecs in the medibuntu repositories which you can enable here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)  You should already have the totem plugin for movies, it's just the codecs you need.  Personally I prefer the mozilla-mplayer plugin so you could also install that and use if you wish.

---

### Post by sisco311 on 2008-04-12
[mozilla-mplayer(click to install)]("apt:mozilla-mplayer")

Or you can install it from Add/Remove or Synaptic Package Manager.

Or the terminal:
```
sudo aptitude install mozilla-mplayer
```

---

### Post by shellymoxley on 2008-04-12
in the terminal how would I apply???

Do I need to uninstall totem to get Mplayer????

---

### Post by sisco311 on 2008-04-12
> **shellymoxley said:**
> in the terminal how would I apply???

Do I need to uninstall totem to get Mplayer????


No, just copy and paste the command in the terminal.
After the plugin is installed restart the browser.

EDIT. You don't need but you can remove the totem-mozilla plugin:
```
sudo aptitude remove totem-mozilla
```

---

