---
title: "Server questions"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by amazon3d on 2007-08-14
Well today I noticed that I know nothing when it comes to "real" servers.  I have a black screen starring me in the face.  I kinda got a feel for the sudo but I'm wondering it there is a GUI to set up the settings on the server or if everything has to be done from the command prompt?
If so how do I access the GUI?

---

### Post by renzokuken on 2007-08-14
do you have X installed? if not you will have to install some sort of desktop environment first before you can use GUIs

```
 sudo apt-get install ubuntu-desktop     # for gnome
 sudo apt-get install kubuntu-desktop     # for KDE
 sudo apt-get install xubuntu-desktop     # for xfce
```

---

### Post by amazon3d on 2007-08-14
Ok i have the desktop installed.  Is there no way for me to manage the FTP/HTTP servers I have running, I have them running but I don't see how I can add directories, and I can't mod a file I need to inorder to prevent anonymous access and only allow registered users. (root is owner)

---

