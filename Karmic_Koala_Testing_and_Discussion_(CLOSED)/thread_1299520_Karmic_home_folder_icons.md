---
title: "Karmic home folder icons"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewpowell on 2009-10-24
I have a question regarding the new home folder icons in Karmic (great addition by the way!). I want to create some new folders in my home folder and put icons on them like the default folders (such as the picture icon on the pictures folder, the document icon on the documents folder, etc.). How do I do this?  I know I can right click, go to properties, and select a different icon for the folder, but that doesn't work right for two reasons.  First, doing it that way assigns a specific, static icon to that folder.  If I change themes it won't change like the default home folders do (for example, if I change from Human to Clearlooks, all the default home folders will change to Clearlooks folders with the appropriate icons, but the one I set manually will still have the Human icon that I selected).  Second, if I drag my new folder onto the left panel of nautilus to make a link, it will just have a generic folder instead of one with the icon I want (if I drag one of the default folders onto the left panel, it will have the appropriate icon there too).  There must be a configuration file somewhere that tells gnome to always associate the documents folder with a theme-appropriate documents folder icon (and pictures, music, videos, etc.).  I tried looking around in gconf-editor for something but didn't have any luck.  Can anyone help me with this?  Thanks in advance.

---

### Post by wolterh on 2009-10-27
I think I have an answer for you.

Create the following file (empty, text) in your ~/.config directory:

user-dirs.dirs
```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_VIDEOS_DIR="$HOME/Videos"

```

---

### Post by lnxguit on 2009-10-27
Thanks woli, that worked perfectly!

---

