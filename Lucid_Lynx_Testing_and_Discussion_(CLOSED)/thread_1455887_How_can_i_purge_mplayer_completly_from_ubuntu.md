---
title: "How can i purge mplayer completly from ubuntu?"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-16
i have installed an svn version MPlayer SVN-r31042-4.4.3 and this versions don't have hebrew font windows 1255 so i can't use it with Hebrew translation and in this case even totem is enaf for me so i need to purge mplayer completely then reinstall the version from
the main repositories  anybody know how?

[http://code.google.com/p/gnome-mplayer/issues/detail?id=382](http://code.google.com/p/gnome-mplayer/issues/detail?id=382)

thanks in advance.

---

### Post by immerohnegott on 2010-04-16
Assuming you compiled and installed from a source tarball, there should be an uninstall script somewhere in the source folder you used to install. try going into terminal, cd-ing to that directory and running

```
sudo make uninstall
```

this works with some programs (in my limited experience, anyway). Otherwise, check the readme and see if there are instructions for removal.

---

