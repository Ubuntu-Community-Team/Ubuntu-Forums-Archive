---
title: "Package search with multiple words"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by fang2415 on 2006-12-06
Every time I search for more than one word at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (e.g., "cd ripper"), I get the following not-very-helpful message:

Error: keyword not valid or missing

Anybody know of a workaround?

Thanks

f2

---

### Post by SyvanX on 2006-12-06
It would probably be easier to just search in the Terminal with apt-cache.

```
$ apt-cache search cd ripper
kaudiocreator - CD ripper and audio encoder frontend for KDE
sound-juicer - GNOME 2 CD Ripper
crip - terminal-based ripper/encoder/tagger tool
cwcdr - Chez Wam CD Ripper
distmp3 - A Perl client and daemon for distributed audio encoding
goobox - CD player and ripper for GNOME
grabcd-rip - rip and encode audio CDs - ripper
grip - GNOME-based CD-player/ripper/encoder
jack - Rip and encode CDs with one command
ripperx - a GTK-based audio CD ripper/encoder
yaret - A console tool to turn CDs into encoded music
```

Otherwise, I don't know how to use a multi-keyword search on packages.ubuntu.com

---

### Post by fang2415 on 2006-12-07
Yeah, good call, the site is just a direct mirror of the command line functionality, isn't it.  Except... broken.  Seems like something a developer should have a look at to ensure we don't drive away any cli-o-phobes...

Anyway, thanks!

f2

---

### Post by SyvanX on 2006-12-07
I didn't have fancy GUIs when I started with linux, so I still use apt :) 

There is a GUI you can search in.

> Applications --> Add/Remove...

There is a search bar in the top of the window.  It returns fewer results than apt but it should work for you.

I don't know why the website doesn't work, but you're right it doesn't make sense to me either.

---

