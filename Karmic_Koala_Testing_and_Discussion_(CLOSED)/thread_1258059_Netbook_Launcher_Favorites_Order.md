---
title: "Netbook Launcher Favorites Order"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2009-09-04
Is there a way to reorder the icons in the favorites section of my netbook launcher?  A while ago I did an update and it removed empathy, now there is just a blank spot there.  If you look in the screen shot you'll see what I mean.  I would like to either get rid of that empty spot or at least reorder my icons so its at the end of the list.

Thanks for your help.

---

### Post by bartaz on 2009-10-28
I just started to play with Netbook launcher and I also found it quite a pain to reorder Favourites.

I found one way to do it.

Open Gnome Configurator editor from command line:
```
gconf-editor
```

and find Netbook launcher configuration there under apps/netbook-launcher

There (under favourites/favourites_list) you have a list of favourites and you can move or delete them.

It's not the best place to add bookmarks as it would be a pain to fill all the properties in this editor but works fine if you really need to reorder them.

After making any changes make sure you restart netbook-launcher.
You can log-in again or simply kill it from command line:
```
killall netbook-launcher
```

---

