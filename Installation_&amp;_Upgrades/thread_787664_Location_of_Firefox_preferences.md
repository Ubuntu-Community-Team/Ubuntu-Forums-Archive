---
title: "Location of Firefox preferences"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by kumoshk on 2008-05-09
I was noticing some bugs with the beta version of Firefox that comes with Hardy (try chatting on Facebook and see what happens; this is one example, anyway)—so, I decided to downgrade to the stable version of Firefox.

After that, I noticed it still had my Flashblock extension installed, and all my preferences. I tried to uninstall it, but for some reason it wouldn't uninstall (I figure it's a bug caused by the wrong version of the extension or something to do with the difference in the extension managers for the two versions). I tried to uninstall Firefox completely, but the preferences and plugins were all still there when I reinstalled them. (Is there really a difference between removing and removing completely?)

Anyway, I can't uninstall the plugin (it doesn't work and I need to uninstall it before I can install one that does).

So, I looked for all my Firefox settings, but nothing I found appeared to have what I need. I looked in the following places, at least:
/usr/bin/firefox
/usr/share/firefox (and all that)
somewhere in /etc/
some lib folder

They all had Firefox things, but apparently, they weren't what I needed.

---

### Post by hermes0710 on 2008-05-09
Search for firefox in your home folder:

```

cd ~
find -name *firefox*

```

In these folders you will find you custom plugins...etc for firefox

---

