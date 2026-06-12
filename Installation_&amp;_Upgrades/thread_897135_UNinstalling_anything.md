---
title: "UNinstalling anything?"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by evrne432 on 2008-08-21
ok so ive downloaded stuff like winff,opera, that i want to uninstall.
i tried searching for them in the package managers but i didnt install them using it so it wont uninstall
how can i uninstall anything?
haha yeah it sounds like a stupid question

---

### Post by Cheesehead on 2008-08-21
Uninstalling properly depends on how you installed it.

Give us a detailed example of how you installed an app (what you clicked on, commands you used, in order, etc), and we'll tell you how to remove it properly.

Be aware that Linux stores libraries and executables and config files and other data and links in different parts of the file tree. So we need to know what you put where.

---

### Post by michaeltobin on 2008-12-12
same here, im pretty new to it all, can some1 please let me know how to uninstall winff from the terminal

---

### Post by crystaldart on 2009-08-21
Seems i Have the same problem. I installed WINFF by sudo apt get  command. authenticated it too as directed in winff site.

But I cant see the programme. May be some error. Now I want to Uninstall it. 
What should I do.

Thank you

---

### Post by Partyboi2 on 2009-08-21
Try using
```
sudo apt-get remove package
``` *change package to actually package name.

---

### Post by paul.gevers on 2009-08-22
> **crystaldart said:**
> Seems i Have the same problem. I installed WINFF by sudo apt get  command. authenticated it too as directed in winff site.

But I cant see the programme. May be some error. Now I want to Uninstall it. 
What should I do.

Thank you

Interested in this problem. Several questions:

- Did the installation go alright (no errors/warnings)?
- Which directives exactly are you talking about (url)?
- See if you have the following files/directories:
  - /usr/share/doc/winff/
  - /usr/share/winff/
  - /usr/bin/winff

Hope I can help...

---

### Post by mmwisner on 2009-09-02
I'm in need here, too--need to uninstall Jhove ([http://hul.harvard.edu/jhove/](http://hul.harvard.edu/jhove/)) which was installed via wget command, tar.gz.

---

