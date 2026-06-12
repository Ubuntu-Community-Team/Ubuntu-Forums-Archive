---
title: "Jaunty + Compiz"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rafaelsousa on 2009-01-28
Has someone managed to sucessfully install compiz + nvidia drivers in Jaunty?

I was able to install nvidia driver, by setting up xorg.conf (using X -configure detected hardware settings), but when I'm in gnome, and, type in terminal:

```
glxinfo |grep rendering
```

It says that the glx module wasn't loaded... But I'm certain that the option

```
load "glx"
```

is in xorg.conf.

Someone has experienced same issue?

---

