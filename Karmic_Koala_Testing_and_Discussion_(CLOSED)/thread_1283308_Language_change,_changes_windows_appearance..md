---
title: "Language change, changes windows appearance."
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Netich on 2009-10-05
Hi, I tried to change the language from Spanish to English. Since then, all nautilus windows appear like the one in the image.

[[IMG]http://img185.imageshack.us/img185/2211/screenshotdavid.th.png[/IMG]](http://img185.imageshack.us/i/screenshotdavid.png/)

btw, i was trying to set all in English, including the home folders (music, videos, etc...) but these folders are still in English. Is this the correct behaviour? I thought these names would be like environment variables, something like $MUSICFOLDER... 

Thanks!

---

### Post by Miguel on 2009-10-05
You may have to look at the files "~/.config/user-dirs.locale" (language, US english is en_US) and you may have to update "~/.config/user-dirs.dirs", without the quotes. Finally, you'll have to run the following commands (I don't know the order):
```

$ xdg-user-dirs-gtk-update
$ xdg-user-dirs-update

```

---

### Post by Netich on 2009-10-05
Thanks, that helps with the folders names, but i still have the windows without toolbar, or the side column. I can reset the to default. And when you double-click in a folder, it opens another window.

Do i have to post a bug in launchpad or something?

---

### Post by mcduck on 2009-10-05
> **Netich said:**
> Thanks, that helps with the folders names, but i still have the windows without toolbar, or the side column. I can reset the to default. And when you double-click in a folder, it opens another window.

Do i have to post a bug in launchpad or something?

Check the Nautilus preferences first, and make sure "Always open in Browser window" (or whatever the setting to switch between spatial and browser mode was called..) is enabled.

---

### Post by Netich on 2009-10-05
I dont know what ive done, but its been fixed. I guess that messing with languages made nautilus lose some configuration. What ive learn today: if something isnt broken, dont try to fix it.

Thanks for your help

---

