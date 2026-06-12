---
title: "Main Menu (alias alacarte)"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Gianl09 on 2009-11-17
This is a funny one. I have installed Ubuntu 9.10 on my 3 computers (work, home and laptop) starting from the same cd. In 2 cases the Main menu editor doesn't work and I get the following messages

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 63, in __loadMenus
    self.save(True)
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 67, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/gianluigi/.config/menus/applications.menu'

If I run "sudo alacarte" the editor appears but it doesn't save the changes. On the laptop instead everything works fine. Anybody can explain what's going on? Thanks

---

### Post by jpeddicord on 2009-11-17
Your permissions on the files/directories are bad. Don't needlessly run things as root. :)

This should fix it up by changing the owner of your config directory back to you:
```
sudo chown -R gianluigi:gianluigi ~/.config
```

---

### Post by Gianl09 on 2009-11-18
Thanks. It works now but I had to change the ownership to .config and .local. The question, however, is why installing on 3 computers from the same live CD I ended up with different permissions on 2 of them.

---

### Post by jpeddicord on 2009-11-18
> **Gianl09 said:**
> Thanks. It works now but I had to change the ownership to .config and .local. The question, however, is why installing on 3 computers from the same live CD I ended up with different permissions on 2 of them.

It's likely that you unintentionally launched a user process as root early on, such as a root file browser. When that happens, any new files created will be owned by root and not by your user account.

---

