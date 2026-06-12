---
title: "GDM Background"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-09-12
I want to change my GDM background to /usr/share/gdm/themes/human/background.png, and my login logo to be as attached. any ideas?
Attached Thumbnails:

---

### Post by ceramicm on 2009-09-12
For the background, use:
```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /usr/share/gdm/themes/human/background.png
```

Not sure exactly what you mean by "login logo." If you are talking about the logo that appears with the progress bar after you log in using GDM and before your desktop is displayed, then do this:
```
 sudo cp /path/to/login_logo.png /usr/share/ubuntu-docs/help/images/C/ubuntuheader.png
```
Be sure to replace "/path/to/login_logo.png" with the actual path!

---

### Post by theozzlives on 2009-09-12
> **ceramicm said:**
> For the background, use:
```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /usr/share/gdm/themes/human/background.png
```

Not sure exactly what you mean by "login logo." If you are talking about the logo that appears with the progress bar after you log in using GDM and before your desktop is displayed, then do this:
```
 sudo cp /path/to/login_logo.png /usr/share/ubuntu-docs/help/images/C/ubuntuheader.png
```
Be sure to replace "/path/to/login_logo.png" with the actual path!

The second one worked, but the first one is to change desktop background not GDM background. Ubuntu is using /usr/share/backgrounds/warty-final-ubuntu.png for GDM.

---

### Post by ceramicm on 2009-09-12
I'm sorry, I didn't know that (about the gconf key only working for desktop background)!

I guess you could always replace /usr/share/backgrounds/warty-final-ubuntu.png with /usr/share/gdm/themes/human/background.png. I overwrote my warty-final-ubuntu.png, and my overwrite shows up in GDM, so I know this works.

---

### Post by theozzlives on 2009-09-13
> **ceramicm said:**
> I'm sorry, I didn't know that (about the gconf key only working for desktop background)!

I guess you could always replace /usr/share/backgrounds/warty-final-ubuntu.png with /usr/share/gdm/themes/human/background.png. I overwrote my warty-final-ubuntu.png, and my overwrite shows up in GDM, so I know this works.

I did that but my background color is still brown at the login screen. I at least want it black. Used to be able to change that in "Login Window" of System > Administration.

---

### Post by theozzlives on 2009-09-13
> **ceramicm said:**
> For the background, use:
```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /usr/share/gdm/themes/human/background.png
```

Not sure exactly what you mean by "login logo." If you are talking about the logo that appears with the progress bar after you log in using GDM and before your desktop is displayed, then do this:
```
 sudo cp /path/to/login_logo.png /usr/share/ubuntu-docs/help/images/C/ubuntuheader.png
```
Be sure to replace "/path/to/login_logo.png" with the actual path!

If your still there, the first one does work! It's just Human instead of human. Thanks for your help!

---

### Post by ceramicm on 2009-09-13
No problem, glad this is finally working for you!

---

