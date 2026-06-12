---
title: "Set global preferences"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by jonchristensen-v on 2013-10-07
How do I go about setting gloabal preferences (don't really know what to call them) so when a new user is created, certain things are automatically configured? For example, when a new user is created and they log in for the first time, I need them to have certain icons in the launcher panel, their default browser should be set and launcher panel icon size set.

Thanks!

---

### Post by MG&amp;TL on 2013-10-07
Per-user preferences are stored in a user's home directory, in so-called "dot files", which are files and directories preceded by a '.' character. These files are not usually shown in file managers, so press Ctrl+H in Ubuntu's default file manager to see them, and again to hide them.

"Global preferences" are files stored in */etc/skel**/* which are copied to a new user's home directory when the user is created. Put files in */etc/skel/* (as root) to set "Global preferences".

Unfortunately there isn't really a standard place where user settings are stored, especially for applications. However, I believe *most* settings are stored as a dconf database file in *<home>**/.config/dconf/user*. It might also be worth checking (and editing) what is in */etc/skel/* by default.

I can go over any of these points if you have problems, although I don't actually have access to an Ubuntu machine at the moment.

---

