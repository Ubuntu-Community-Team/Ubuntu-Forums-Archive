---
title: "GDM looks bad compard to the loading screen"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Glenn nl on 2009-09-20
The new loading screen is really really pretty.
But then the new gdm pops up and it really doesnt fit the new loading screen.
How about getting the brown shiny background from the loading screen and add a fitting gdm colour.


[ATTACH]129148[/ATTACH]
[ATTACH]129149[/ATTACH]

---

### Post by jfernyhough on 2009-09-20
It hasn't been themed yet. Remember, this is a work in progress...

You could always do the theme and submit it, you know. ;)

---

### Post by GeorgeVita on 2009-09-20
... I am sure that 'theme developers' have the answer and they keep it for the end of October!

We have to wait a little bit!

**EDIT:** thanks to **Longinus00**, it is better now!

---

### Post by Longinus00 on 2009-09-20
If you want to change the wallpaper that is displayed in the login screen, it is located at
```
/usr/share/backgrounds/warty-final-ubuntu.png
```

Interestingly enough, even though the filename is .png, the file is in fact a jpeg. To simply copy over the xsplash background, run the following command.

```
$ sudo cp /usr/share/images/xsplash/bg_2560x1600.jpg /usr/share/backgrounds/warty-final-ubuntu.png
```

---

### Post by glasen on 2009-09-20
Or just type in the following line :

```
sudo -u gdm gconftool-2 --type string --set /desktop/gnome/background/picture_filename /usr/share/images/xsplash/bg_2560x1600.jpg
```

---

### Post by Marat89 on 2009-09-20
Thank you!
Now Karmic looks very professional 

SLICK:guitar:

---

### Post by cyberkilla on 2009-09-20
> **Longinus00 said:**
> If you want to change the wallpaper that is displayed in the login screen, it is located at
```
/usr/share/backgrounds/warty-final-ubuntu.png
```

Interestingly enough, even though the filename is .png, the file is in fact a jpeg. To simply copy over the xsplash background, run the following command.

```
$ sudo cp /usr/share/images/xsplash/bg_2560x1600.jpg /usr/share/backgrounds/warty-final-ubuntu.png
```

And "Warty" is a bit obsolete too. That should probably change, for consistency's sake.

---

### Post by Longinus00 on 2009-09-20
> **glasen said:**
> Or just type in the following line :

```
sudo -u gdm gconftool-2 --type string --set /desktop/gnome/background/picture_filename /usr/share/images/xsplash/bg_2560x1600.jpg
```

That might change your desktop background but I don't think that will change the background of the login window.

---

### Post by jfernyhough on 2009-09-20
The key is "-u gdm". It's running gconf-editor for the gdm "user" and changing its background. This should change the background for gdm.

---

### Post by Longinus00 on 2009-09-20
> **jfernyhough said:**
> The key is "-u gdm". It's running gconf-editor for the gdm "user" and changing its background. This should change the background for gdm.

Ahh, overlooked that.

---

