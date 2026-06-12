---
title: "X11 Mouse theme only works in Firefox."
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Talynz on 2010-08-08
It changes from the cool cursor to the default cursor on the desktop and windows. The custom cursor only shows in Firefox? How do I fix this??

---

### Post by hasanaa on 2010-08-09
```
sudo gedit /usr/share/icons/default/index.theme
```
change the cursor theme name, save and close. then:
```
compiz --replace
```

---

### Post by vince2678 on 2010-08-20
Compiz cannot update the mouse cursor theme when it is updated in GNOME.    Install this package to allow compiz to notice the change and feel   free  to modify it however you want. PLEASE read he control info!

Unfortunately only works with GNOME. If anyone has LXDE and XFCE please    send me info on how it stores info about cursor theme and size and the    program used for changing cursor theme. I have KDE in a VM so I'll  try   something there.
 
 LINK: [_http://ubuntuforums.org/showthread.php?t=1557297_]("http://ubuntuforums.org/showthread.php?t=1557297")

READ CAREFULLY!

---

### Post by 5oak on 2010-12-15
> **hasanaa said:**
> ```
sudo gedit /usr/share/icons/default/index.theme
```
change the cursor theme name, save and close. then:
```
compiz --replace
```

Pfff it took me like two hours to find your post. Thank you!:)

---

