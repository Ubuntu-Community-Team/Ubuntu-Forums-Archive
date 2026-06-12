---
title: "usb and panel in Xubuntu"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by MarkLori on 2006-02-25
Just installed Xubuntu and Automatix.  After I installed Automatix my panel disappeared.  That is not a terrible thing but I did like the convenience and the appearance of it centered at the bottom of the screen.

Also I do not see my external usb drive when I plug it in.  This was not a problem in Warty.  I plugged it in and it just appeared on the screen.  Guess I'm spoiled. 

Thanks for any help.

Mark

---

### Post by direwolf on 2006-02-25
[QUOTE=MarkLori]After I installed Automatix my panel disappeared. That is not a terrible thing but I did like the convenience and the appearance of it centered at the bottom of the screen.[/QUOTE]

Start with a clean session. (no other apps running yet)

Right-click on the desktop and choose "Run program..." 
enter the following command 
```
xfce4-panel
```

[QUOTE=MarkLori]Also I do not see my external usb drive when I plug it in.[/QUOTE]
XFCE doesn't mount volumes automagically (like GNOME). If you still have all the GNOME packages installed you can get them to mount automagically (they won't show up on the desktop but they will be mounted) ... 
*note: you will still have to unmount them manually using "sudo umount /your/mountpoint" (no quotes & where /your/mountpoint equals the the location the drive was mounted)

Right-click on the desktop and choose "Run program..." again 
enter the following command 
```
gnome-volume-manager
```

then save your session and logout

---

### Post by MarkLori on 2006-02-27
:) 

Thanks very much!  I knew it had to be something simple.

---

