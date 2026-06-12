---
title: "Can't edit menu's in 9.10"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by setherd on 2009-07-21
I am cleaning up my hom directory and removing some wine programs I don't use. they are still listed on my menu so I thought I'd just right click on the menu and select "edit".
well that crashes Main Menu every time. and I can't run alacarte as a user.

```

seth@linux:~$ alacarte 
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/seth/.config/menus/applications.menu'
seth@linux:~$ 


```

is this happening to anyone else?

---

### Post by taavikko on 2009-07-21
like the last line states, error with permissions,
check that the file is owned by you and not root.
```
ls -l ~/.config/menus/applications.menu
```


It's working correctly here.

HOWTO: [http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8](http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8)
Remove wine entries from menus

---

### Post by sisco311 on 2009-07-21
nm, i'm too slow

---

### Post by setherd on 2009-07-21
thanks! I missed that. Turns out a lot of my home directory permissions are screwed up, not sure when it happened. Root took over a lot.

---

