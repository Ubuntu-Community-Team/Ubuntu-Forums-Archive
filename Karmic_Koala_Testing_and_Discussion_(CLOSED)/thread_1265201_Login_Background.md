---
title: "Login Background"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-09-13
I want my login Background to look like attached. I already figured out before and after, but the background at the login window is just brown. I'd settle for at least black.

---

### Post by MacUntu on 2009-09-13
The background of GDM is the background of the user 'gdm', so what you do is:

[LIST]
[*] log out,
[*] log in at a terminal (eg. Ctrl+Alt+F1),
[*] start gnome-control-center as user 'gdm':
```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```
[*] go back to the login screen (Ctrl+Alt+F7) where gnome-control-center should be started, and
[*] configure the theme how you like it.
[/LIST]

---

### Post by theozzlives on 2009-09-13
> **MacUntu said:**
> The background of GDM is the background of the user 'gdm', so what you do is:

[LIST]
[*] log out,
[*] log in at a terminal (eg. Ctrl+Alt+F1),
[*] start gnome-control-center as user 'gdm':
```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```
[*] go back to the login screen (Ctrl+Alt+F7) where gnome-control-center should be started, and
[*] configure the theme how you like it.
[/LIST]

Well that didn't work

---

