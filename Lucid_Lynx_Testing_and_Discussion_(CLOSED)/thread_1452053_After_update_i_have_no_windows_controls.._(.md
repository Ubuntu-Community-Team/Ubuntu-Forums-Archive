---
title: "After update i have no windows controls.. :("
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by leeman101 on 2010-04-11
few days ago i installed all recommended and security updates for Lucid Lynx, and ever since then i have had no window border and no window controls for any window, and the window manager will not open...  does anyone know what could be causing this? i have searched and searched but have found nothing to solve this.  Any help would be appreciated  :)

---

### Post by dino99 on 2010-04-11
try with:

sudo apt-get install -f
sudo dpkg --configure -a

check that ubuntu-desktop is installed too

can look at /var/log for errors

---

### Post by leeman101 on 2010-04-11
Tried the commands but it didnt seem to change anything..
It seems that Metacity will not run for some reason..

---

### Post by leeman101 on 2010-04-11
Okay so if i type "metacity" in the terminal, the windows all have borders and controls again, but when i reboot there are no borders, etc.  so basically metacity does not run automatically like it should when Ubuntu starts.
after typing metacity in the terminal this is what the terminal says:
[COLOR=Blue][I]
Window manager warning: "<Super>" found in configuration database is not a valid value for keybinding "panel_main_menu"[/I][/COLOR]

[COLOR=Black]Im not sure if this is causing the auto-start problem or not...  the window manager will run after i tell it to, but not automatically.[/COLOR]

---

### Post by obscur156 on 2010-04-11
Hi,to make sure metacity starts when you boot just add metacity to satup program.

Go to    System/Preference/Startup application     and add metacity to the list by clicking "add"    name = metacity and "command" metacity.

Your done,now it will start at startup automaticaly.

Best regards.

---

### Post by kansasnoob on 2010-04-11
See what happens if you reinstall metacity:

```
sudo apt-get install --reinstall metacity
```

There was a partial upgrade problem recently regarding compiz and metacity, I don't recall the specifics, but I just waited about 24 hours until the "partial upgrade" thing resolved itself before updating.

---

### Post by leeman101 on 2010-04-11
Thanks Obscur, that was pretty simple and it worked.. usually i would have thought of that, i guess i thought the program was crashing but it just wasnt starting.  :)
thanks guys.

---

### Post by obscur156 on 2010-04-11
My pleasure leeman101 ,its always fun to help others.

Have a nice day and long live Ubuntu. :)

---

