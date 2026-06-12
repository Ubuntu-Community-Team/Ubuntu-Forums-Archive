---
title: "moving files to Wine folders"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by xjgnsdof on 2007-06-02
How do I move files to Wine folders? Specifically, I want to move a file to a folder in C:\Program Files that exists in Wine, but not in my Windows partition.

---

### Post by Ken_Lewis81 on 2007-06-02
Wine hides its "pretend C:\ drive" in your home directory, hidden behind a '.'  The full path is ```
~/.wine/drive_c/
``` where the ~ is linux shorthand for your user's home storage, whatever your username.

Take care.
Ken.

---

### Post by Linkerator on 2007-06-02
If you would want to do it while being able to see your files, go to your home folder, then hit Ctrl+H. This will unhide all of your files. Now search for wine by typing " .wine " and you have the folder.

---

