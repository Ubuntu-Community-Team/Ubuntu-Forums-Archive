---
title: "Jaunty Notifications Dont Work"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mjheagle8 on 2009-03-29
i recently updated to jaunty beta from intrepid. my notifications are still the old ones, and i would really like to have the new ones. how do i get the new ones? is there something i need to do/fix to make the new notifications work? i am using compiz.

---

### Post by BobCFC on 2009-03-30
Make sure you have a package called **notify-osd** installed, either look for it in synaptic or type

```
sudo apt-get install notify-osd
```


Then log out and log back in


EDIT: Also the new notification icons are only in the Human theme, if you want to use a different icon theme then copy all of the notification-xxx icons from the Human/scalable/status folder to the new themes status folder such as

```

cp /usr/share/icons/Human/scalable/status/notification-* /home/me/.icons/mytheme/scalable/status
```

---

### Post by aamukahvi on 2009-03-30
> **BobCFC said:**
> EDIT: Also the new notification icons are only in the Human theme, if you want to use a different icon theme then copy all of the notification-xxx icons from the Human/scalable/status folder to the new themes status folder such as
The beautiful [GNOME-colors]("http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562") icon set has the notification icons also :) They quote "Full notify-osd compatibility" since v2.6.

---

