---
title: "No 'desktop' / launcher, just plain wallpaper"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by meneedhelp on 2011-04-05
I just had my pc updated with the latest Ubuntu 11.04.. 
but since im very curious with the new appearance (which i think really nice and neat), i started to configure Compiz and opened the 'compiz configuration setting manager'.

since i thought it was OK, i just changed the desktop configuration to 'Desktop cube' just like on my previous Ubuntu (10.10).. and i just clicked to change to desktop cube whatever popped there to confirm it.

but later i found i can't open any programs anymore, just plain wallpaper on my 'desktop'. :confused:

so could anyone help me to restore the previous settings? even shortcuts doesn't help.
sorry newbie here. :(

any help would be much appreciated!

thanks in advance! :)

---

### Post by d3vans on 2011-04-05
this link might help u..

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by meneedhelp on 2011-04-05
> **d3vans said:**
> this link might help u..

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

hi d3vans, thanks for the help.
but like i said, no shortcuts could help me.
i tried earlier alt + f2 .. ctrl + alt + t but nothing happened. they won't appear! :(

---

### Post by d3vans on 2011-04-05
try this one then..

[http://www.omgubuntu.co.uk/2010/08/restore-default-gnome-settings-in-ubuntu-quick-tip/](http://www.omgubuntu.co.uk/2010/08/restore-default-gnome-settings-in-ubuntu-quick-tip/)

hope it helps

---

### Post by meneedhelp on 2011-04-05
> **d3vans said:**
> try this one then..

[http://www.omgubuntu.co.uk/2010/08/restore-default-gnome-settings-in-ubuntu-quick-tip/](http://www.omgubuntu.co.uk/2010/08/restore-default-gnome-settings-in-ubuntu-quick-tip/)

hope it helps

wow.. thanks! this one does the magic! :D
it works for me with the 2nd one:
*rm .gnome .gnome2 .gconf .gconfd .metacity -rf*


*mkdir gnome_backup; >> can't create one. it says already exist.*
[I]mv .gnome .gnome2 .gconf .gconfd .metacity gnome_backup/ >> doesnt work either..

[/I]thank a lot d3vans. cheers! :)

---

