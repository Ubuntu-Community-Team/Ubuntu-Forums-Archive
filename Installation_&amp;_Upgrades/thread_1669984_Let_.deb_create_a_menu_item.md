---
title: "Let .deb create a menu item"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by JanBart on 2011-01-18
Hello,

I wrote [a little program]("https://code.google.com/p/woordjes/") and an installer(.deb) for it.
The installer does its job excellently and after running the installer, the program is installed.

However, there are two things that refuse to work.

A) Although the Woordjes.desktop file is copied into /usr/share/applications and when clicking it, it starts the program; the menu-item itself is not showing up in the main menu. 

B) I'm running the debuild script to make the installer on a AMD64 pc. I found out i'll have to use a i386 pc to make it installable on a i386 pc although I coded that it should work on "all" systems.

My Woordjes.desktop file:
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Comment=Practice your vocabulary!
Comment[en_US]=Practice your vocabulary!
Exec=java -jar /usr/share/woordjes/Woordjes.jar
Icon=/usr/share/woordjes/icon.xpm
Icon[en_US]=/usr/share/woordjes/icon.xpm
Name=Woordjes
Name[en_US]=Woordjes

```

What am I doing wrong?

Thanks in advance.

---

