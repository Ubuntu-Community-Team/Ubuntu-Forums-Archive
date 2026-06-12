---
title: "jaunty and nvidia"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sefs on 2009-04-16
I have enabled the nvidia 180 restriced driver from my nvidia card.  in nvida-settings I set it to 1280x1024 ... it stays at this resolution until my next reboot.  How can I get my native resolution to persist.

---

### Post by jbrown96 on 2009-04-16
Try saving it to your xorg.conf file. Alt+F2 ```
gksu nvidia-setttings
``` Set you resolution and then there should be an option to save your configuration.

---

### Post by James_Lochhead on 2009-04-17
The problem with the NVidia settings is that by default the menu item has the wrong permissions to allow saving of the file. Edit the menu item so that it has gksudo or gksu in front of nvidia-settings (as above) and it will work if you click "save file".

---

### Post by sefs on 2009-04-17
That has never work for me in any version of ubuntu including jaunty.

The error I am getting which I am getting now with or without gksu is

```

Failed to parse existing X config file '/etc/X11/xorg.conf'!

```

Is there some other adjustment I have to make?

---

### Post by Bachstelze on 2009-04-17
Moved to Jaunty Testing and Discussion.

---

### Post by caryb on 2009-04-17
Not sure if this works in Gnome but in Kubuntu you right click on the menu button on mine it's the K button & select menu editor on the Nvidia settings tick the box that says run as other user & type in root. & Bingo it prompts for a password & will save user settings.

Cary

Hopefully someone can translate my ramblings to Gnome speak:lolflag:

---

