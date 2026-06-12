---
title: "How to change Distributor Logo?"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by IndyGunFreak on 2010-04-24
Used to be, it was simply changing the picture in the theme or icon set.. now, I can't find distributor-logo in my current icon theme.

---

### Post by IndyGunFreak on 2010-04-24
Surely somebody has tried to do this....

---

### Post by x-shaney-x on 2010-04-24
It may depend on the icon theme but the default ubuntu icon theme uses "start-here.svg"

To avoid it getting overwritten with future updates you can mirror the path to the start-here icon in the .icon folder in your home directory.

Example:

System path to start-here.svg for the default ubuntu theme is ```
/usr/share/icons/ubuntu-mono-dark/apps/24/start-here.svg
```So if you create the directories in your home/.icons directory it will be like this ```
/home/yourusername/.icons/ubuntu-mono-dark/apps/24/start-here.svg
```this structure will ONLY contain the start-here icon (and any others you want to replace).

Incidentally, you can also use a .png icon called start-here.png
I actually put both in the folder and it used the .png rather than the .svg

Hope all that made sense.

---

### Post by gexi on 2010-04-24
well, you could also install ubuntu tweak. this makes it somehow easier. if you have lucid installed, just go to terminal and add the tualatrix ppa by typing

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

start ubuntu-tweak and then, under gnome-settings (?) you can just change the menu-icon.

---

### Post by Mr. Picklesworth on 2010-04-24
The default icon theme is Humanity. You can find the icon with Nautilus's search feature. Just go to the /usr/share/icons/Humanity, press the Search button and type distributor-logo.

GDM probably uses the big one, so that's in /usr/share/icons/Humanity/places/64

---

### Post by wojox on 2010-04-24
Open the Alt+F2 and type: gconf-editor
Go to "apps" -> "panel" -> "objects"
Find the right object. Under "object type" it should say "menu-object"
Once you have found the right object, check the box that says "use-custom-icon"
Then right click where it says "custom-icon" and click "Edit Key"
type in the location of the icon and click ok.

---

### Post by x-shaney-x on 2010-04-24
> **wojox said:**
> Open the Alt+F2 and type: gconf-editor
Go to "apps" -> "panel" -> "objects"
Find the right object. Under "object type" it should say "menu-object"
Once you have found the right object, check the box that says "use-custom-icon"
Then right click where it says "custom-icon" and click "Edit Key"
type in the location of the icon and click ok.


As far as I know, that only changes the icon for the combined gnome menu (the single icon rather than menubar).

Ubuntu tweak sounds the easiest option.

---

### Post by IndyGunFreak on 2010-04-25
> **x-shaney-x said:**
> As far as I know, that only changes the icon for the combined gnome menu (the single icon rather than menubar).

Ubuntu tweak sounds the easiest option.

The problem seems related to particular themes, Ubuntu Tweak will not work w/ certain themes, but works fine w/ others.. not sure why that is.


I think your first suggestion is the way to go.

---

