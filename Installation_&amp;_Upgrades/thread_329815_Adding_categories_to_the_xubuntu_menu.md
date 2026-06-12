---
title: "Adding categories to the xubuntu menu"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2007-01-02
Hi all,

I've just installed Xubuntu and I'm trying to add zsnes to the part of the xfce menu between the spacers. I found this [link]("https://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/")  on how to add icons on another part of the foum and this works but I can't find out how to add a new category. When I put 

```

[Desktop Entry]
Version=1.0
Type=Application
Encoding=UTF-8
Name=Zsnes
Comment=Super Nintendo Emulator
TryExec=zsnes 
Exec=zsnes %F
MimeType=text/plain
Categories=Applications;Games;
Icon=/usr/share/pixmaps/zsnes.xpm

```

It puts it under Other rather than creating a Games category. 

Has anyone any ideas?

---

### Post by mikeym on 2007-01-02
The problem was that the names didn't correspont to what was in the menu. By installing another game I was able to see that the category for the *Games* folder was *Game*.

---

