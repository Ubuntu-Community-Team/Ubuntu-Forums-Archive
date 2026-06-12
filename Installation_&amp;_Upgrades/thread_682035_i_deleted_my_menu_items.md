---
title: "i deleted my menu items"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by liakosantonios on 2008-01-29
hi to all,

after giving this command "sudo rm -r skype.desktop /usr/share/applications" i lost almost all of my menu items, can anyone help me to restore them?
i have only Applications=>Internet=>Fire starter and System=>Administration=>Login Window
i have no idea.....

how can i restore the default menu?

---

### Post by c0mp13371331337 on 2008-01-29
With a little bit of searching, you should be able to find the files/directories where the menus are generated.  I'd do a bit of google searching, but deleting those particular files and directories (and probably a reboot, for good measure, at least an X restart) should restore the defaults.  You could even find the global locations of those files and restore them to your home folder.  Any number of ways of doing it should *theoretically* work.  Never had to do it myself, so I'm not sure.  But most software issues in linux can be solved by restoring defaults, usually by deleting the program's config directory from the user's home.

---

