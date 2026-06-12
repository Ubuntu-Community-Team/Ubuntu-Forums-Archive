---
title: "Oxygen icon theme won't install properly after Lucid upgrade"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Dingbats on 2010-06-16
I just upgraded from Karmic to Lucid.  Everything seems to work, except that I have two broken packages, kde-icons-oxygen and kdebase-runtime.  I need KDE installed to run KTorrent.  When I try to reinstall them in Synaptic, I get this error message (in Swedish):

> E: /var/cache/apt/archives/oxygen-icon-theme_4%3a4.4.2-0ubuntu2_all.deb: kunde inte skapa säkerhetskopierad länk av "./usr/share/icons/oxygen/22x22/actions/go-first-view-page.png" innan den nya versionen installeras

Translated:

> E: /var/cache/apt/archives/oxygen-icon-theme_4%3a4.4.2-0ubuntu2_all.deb: could not create backup link of "./usr/share/icons/oxygen/22x22/actions/go-first-view-page.png" before the new version is installed

When I click "details" in the next window, there's terminal output that I can't copy, that just complains about there being something that can't be done with the KDE packages.

All of this results in KTorrent starting without a window manager.

How can I repair these broken packages and make it work?

EDIT:  An fsck fixed it.

---

### Post by Dingbats on 2010-06-16
Looking through the terminal output, I understand that the source of the problem is exactly what the first error message says: a backup of ./usr/share/icons/oxygen/22x22/actions/go-first-view-page.png can't be created, so the oxygen icons won't install, which makes it impossible to configure several KDE packages, and in the end the installation of a few crucial packages fails.

So how can I solve that problem, and have it create that backup?

---

### Post by Dingbats on 2010-06-16
Could the problem be that /usr/share/icons/oxygen/22x22/actions/go-first-view-page.png is corrupt?  Because Eye of Gnome won't open it ("can't open stream").  Does anyone know where I can find a proper version of that file?

Lots of packages depend on oxygen-icon-theme, so at the moment I can't almost install anything.

---

### Post by Dingbats on 2010-06-16
> **Dingbats said:**
> Could the problem be that /usr/share/icons/oxygen/22x22/actions/go-first-view-page.png is corrupt?  Because Eye of Gnome won't open it ("can't open stream").  Does anyone know where I can find a proper version of that file?

Lots of packages depend on oxygen-icon-theme, so at the moment I can't almost install anything.
However, I can't do anything to go-first-view-page.png.  Whatever I do, it says "operation not permitted", even as root.  ls -l returns:

?-wSrwx--- 440 26112 61835 2389104782 1945-10-28 05:29 go-first-view-page.png

Does anyone know anything about this?

---

### Post by Dingbats on 2010-06-16
Clarification: I can install absolutely nothing until this is fixed, apparently.

Is there anyone who has any clue what might be going on?

---

