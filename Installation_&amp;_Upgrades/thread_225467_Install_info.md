---
title: "Install info"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by NetJumper on 2006-07-29
****Where is install info saved?

Hi all.  I have an app that failed during install and can't seem to be cleared.  DOes anyone know where install config data gets saved during package installs?  This one asked some questions and I made an error but now it always used the incorrect data and I can't seem to fix it.  There must be a file somewhere that has this info that I can delete or edit.

Any help would be appreciated greatly!

---

### Post by Ziox on 2006-07-29
what program are you talking about?

and most likely the config. is in your home dirctory.../home/usrname...it should be one of those hidden files...hit ctrl+h to see all the files

---

### Post by peabody on 2006-07-30
I agree that most config information is in your home directory, prefixed with a '.' (which marks a file as hidden in Unix-like OSes).  You'd have to know something about the program to know where it keeps it's data.

Alternatively, since you mentioned that this was during an installation, if you can remember the package name, you might try:

$ sudo dpkg-reconfigure <package name>

which will walk you through the menu for the package configuration if it had any.

---

