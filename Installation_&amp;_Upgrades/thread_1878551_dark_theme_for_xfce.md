---
title: "dark theme for xfce"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-11-10
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

i found this "aud-Default" theme on my system and sort of had to reverse engineer where it came from...

alt + f2

gnome-terminal

run

then if you dont have audacious drop this block of code

```
sudo apt-get install audacious
```

then link the system theme up

```

cd /usr/share/themes
sudo cp -rf /usr/share/audacious/Skins/Default/ ./aud-Default

```

then 

alt + f2

xfce4-appearance-settings

run

then select "aud-Default" for a dark xfce theme

(then add PPA to make audacious audacious 3, it uses gtk3 and breaks this theme from audacious 2)

i just found out my laptop's volume keys DO work, but only under gnome...  (there are bindings for laptop play pause forward backward keys / remotes in the audacious 3 ppa and possibly 2...  general plugins global hotkeys)  this looks reassuring though ill be back if it does not work out.  i need my viewing experience heavy metal black, its easy on the eyes.

in the theme dialogs for gnome click "customize" the default theme, and aud-Default should show up as an option and cross over its death metal black to gnome ;-)  i find my mac keyboards volume keys also function correctly now too

i guess ill throw in some voodoo pictures here....

[img]http://img525.imageshack.us/img525/6308/bigfol.jpg[/img]
[img]http://img802.imageshack.us/img802/4084/magiccircle.jpg[/img]
[img]http://img94.imageshack.us/img94/5686/pentacle.jpg[/img]

---

