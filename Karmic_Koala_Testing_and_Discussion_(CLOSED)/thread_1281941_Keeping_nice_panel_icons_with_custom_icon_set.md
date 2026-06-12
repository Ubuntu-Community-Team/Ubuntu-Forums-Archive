---
title: "Keeping nice panel icons with custom icon set"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by themusicalduck on 2009-10-03
I was just wondering if it's possible to have the nice new karmic volume, network, mail icons for the panel, but while using a custom icon set?

I'd like to use the dust icon set, but it changes the panel icons to ugly defaults, whereas I'd rather keep the nice new karmic icons.

I looked through the folder containing the dust icons, but couldn't actually find the icons it is replacing them with, so it looks like it's finding them from elsewhere.

---

### Post by blackened on 2009-10-03
If the set includes icons for battery/network-manager/volume, then you will probably have to replace each of those individually. If it uses the default Human or Gnome icon set for those three icons, then you can just change the set's inheritance settings:

Navigate to the folder where your icons are and open the index.theme file.

```
[Icon Theme]
Name=Eikon
**Inherits=Humanity,gnome,hicolor**
Comment=Personal icon mix by "What is in a name?".
Directories=scalable/actions,scalable/apps,scalable/places,scalable/places/32,scalable/mimetypes,scalable/devices,scalable/emblems,scalable/emblems/badges,scalable/emblems/32,scalable/emblems/24,scalable/emblems/22,scalable/emblems/16,scalable/stock,scalable/categories,scalable/status,scalable/status/16,scalable/status/22,scalable/status/24,scalable/status/32,scalable/status/64
```

Add Humanity to the bolded line like mine has. Yours won't look exactly like this, but since I don't have the dust set and am too lazy to download it, this should work as an example.

Remember that, by changing the Inherit settings, any icons not included in the top-level set will default to the next level of inheritance.

---

### Post by Tibuda on 2009-10-03
There is a dust icon set? I never seen it, only the Gtk/Metacity theme. Do you have a link?

---

### Post by Seventh Reign on 2009-10-03
These are the two I know of.

[http://gnome-look.org/content/show.php/Dust+Karmic+Iconset+by+mickyz?content=106084]("http://gnome-look.org/content/show.php/Dust+Karmic+Iconset+by+mickyz?content=106084")

[http://gnome-look.org/content/show.php/Meliae-Dust?content=93759]("http://gnome-look.org/content/show.php/Meliae-Dust?content=93759")

---

### Post by themusicalduck on 2009-10-03
Cheers blackened that worked perfectly :D Although for some reason I still have the ugly large black ethernet icon from the alpha instead of the new one, not sure why that is. I'm fully updated too.

This seems to be the right set: [http://linux.softpedia.com/get/Desktop-Environment/Themes/Dust-Karmic-Iconset-49540.shtml](http://linux.softpedia.com/get/Desktop-Environment/Themes/Dust-Karmic-Iconset-49540.shtml)

Edit: Seventh Reign found it first ^^

---

