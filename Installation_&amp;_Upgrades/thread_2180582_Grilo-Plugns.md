---
title: "Grilo-Plugns"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by aaronschillings on 2013-10-13
I'm trying to get DLNA playback support up and running on Ubuntu 13.04.  When I type "sudo apt-get install grilo-plugins-0.1" in my terminal, I get an error saying no package found.  When I do a search for the proper package name, the only thing I can find is that exact name and am unable to get grilo installed and running on my box.  What am I missing??

---

### Post by Bashing-om on 2013-10-13
aaronschillings; Hi ! Welcome to the forum .

For version 13.04 I show:
```

sysop@1304mini:~$ apt-cache search grilo
gir1.2-grilo-0.2 - Framework for discovering and browsing media - GObject introspection data
grilo-plugins-0.2 - Framework for discovering and browsing media - Plugins
libgrilo-0.2-1 - Framework for discovering and browsing media - Shared libraries
libgrilo-0.2-bin - Framework for discovering and browsing media - Binaries
libgrilo-0.2-dev - Framework for discovering and browsing media - Development files
libgrilo-0.2-doc - Framework for discovering and browsing media - Documentation
totem-plugins-extra - Extra plugins for the Totem media player
sysop@1304mini:~$ 

sysop@1304mini:~$ apt-cache search grilo-plugins
grilo-plugins-0.2 - Framework for discovering and browsing media - Plugins
sysop@1304mini:~$ 

```

Appears that version 0.1 has been superceeded and as such is not in the repository -> "error saying no package found".

[INDENT][INDENT]that should help
[/INDENT][/INDENT]

---

### Post by aaronschillings on 2013-10-13
You would think I would have thought to do a cache search before trying to do this! Thanks for the help :)

---

### Post by Bashing-om on 2013-10-13
aaronschillings; Hey !

We are all learning, and sometimes it is the simplest of things that catch us the shortest.

[INDENT][INDENT]it's ubuntu, we are all in this together
 [/INDENT][/INDENT]

---

