---
title: "Menu Broken"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2010-10-18
Hi All -
I installed 10.10 64bit the other day. While everything works fine, I have noticed that the System-->Preferences-->Main Menu is broken. I click on it, but never see the GUI for the Main Menu pop up. Any ideas how to fix that?

I will appreciate all your help.

Thanks,
Dhaval

---

### Post by heyandy889 on 2010-10-18
Huh.

I would try rebooting the computer. Sometimes that does the trick.

Maybe something with the panel (task bar) is wrong? You can right click on the panel and say "Add to Panel," and then grab "Main Menu." Might be different names in 10.10, I'm on 10.04.

Additionally, the default keyboard shortcut for the menu is "Alt-F1." So, maybe the menu will open up if you use that keyboard shortcut.

Good luck,
heyandy889

---

### Post by Barriehie on 2010-10-19
In the terminal try:
```

update-menus
```

---

### Post by dhavalbbhatt on 2010-10-19
> **Barriehie said:**
> In the terminal try:
```

update-menus
```


Thanks guys for chiming in - however, let me add a bit more clarity (now that I know more) - the problem is with alacarte the menu editing tool in gnome. I have reinstalled it a couple of times, but that has obviously not helped. I have not had the courage to remove it completely and re-install it, but maybe I should do that.

The other thing that I have done is run "gksu alacarte" from the terminal. That has at least brought up the menu editing tool, but I can't save the changes that I make - so something is obviously broken. I researched the web a little bit and seems like this was a problem a long time ago (alacarte 0.8 - it is now on 0.13.2) but was fixed in 0.9. I am not sure if this has regressed - it obviously feels like that.

Again, thanks for looking - but I will appreciate if anyone has more insight into this.

Thanks,
Dhaval

---

### Post by sergeij on 2010-10-24
hi all, 
I found the same problem (in Ubuntu 10.10 64bit) with my Menu Editor, I ran the "alacarte" command in terminal, it returned 
```
sergeij@sergeij:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_AG

```I tried to unistall, reinstall, reboot system and any other thing you suggested here, but it is not working... 
may you help me??

---

