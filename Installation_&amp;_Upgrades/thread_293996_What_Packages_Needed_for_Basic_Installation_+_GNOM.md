---
title: "What Packages Needed for Basic Installation + GNOME (Solved)"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by edwin11 on 2006-11-06
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi all,

OK, what i am trying to achieve is a very basic installation, with a graphical desktop (X and GNOME), synaptic, but no applications to start with, then install the applications only as i need them.

i understand that i should first start with the server install, then add the basic graphical environment. But the question is what are the minimal packages to add to get a GNOME desktop?



TIA and Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by insub2 on 2006-11-06
i did a quick search and found [http://www.ubuntuforums.org/showthread.php?p=883528](http://www.ubuntuforums.org/showthread.php?p=883528)

from this i gather you should try:
```
sudo apt-get update
sudo apt-get install gnome gdm x-window-system-core icewm menu synaptic xterm
```

but that is mostly a guess and it will install other packages with gnome.
You could try it and see if you like it and if you don't try something else....


an option (a rather _tedious!!_ option) is to install ubuntu and xfe and open up synaptic and select all the istalled packages you don't want and remove them.

---

### Post by edwin11 on 2006-11-06
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Thanks insub2,

> **insub2 said:**
> from this i gather you should try:
```
sudo apt-get update
sudo apt-get install gnome gdm x-window-system-core icewm menu synaptic xterm
```

but that is mostly a guess and it will install other packages with gnome.
You could try it and see if you like it and if you don't try something else....


The WM that comes with a standard Ubuntu install is Metacity right? Is it correct to say that IceWM and Metacity are substitutes?

Also, if i'm not wrong, there's one particular "gnome-something" package that is used to pull in the standard install applications (Gaim, OpenOffice, Gimp, etc). i think that's one to be avoided.


> **insub2 said:**
> an option (a rather _tedious!!_ option) is to install ubuntu and xfe and open up synaptic and select all the istalled packages you don't want and remove them.

Nah, i won't wanna do that! :p


Anyway, i'll be trying out on a VM... so no harm doing some trial & error. i'll try out the above suggestion and let you know!



Thanks and Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by aysiu on 2006-11-06
You might want to start with just this: ```
sudo aptitude update
sudo aptitude install gnome-applets gnome-control-center gnome-icon-theme gnome-menus gnome-panel gnome-session gnome-terminal metacity nautilus gdm x-window-system-core
```

---

### Post by edwin11 on 2006-11-08
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]> **aysiu said:**
> You might want to start with just this: ```
sudo aptitude update
sudo aptitude install gnome-applets gnome-control-center gnome-icon-theme gnome-menus gnome-panel gnome-session gnome-terminal metacity nautilus gdm x-window-system-core
```

This is good. i really ended up with a bare GNOME desktop. Only problem is that when i tried to shutdown by using System -> Quit, nothing happened (usually we get the menu to select Shutdown, Restart, Hibernate, etc.)

So i installed an additional package suggested by insub2 - menu - and the problem is solved. :)

Thanks insub2 and aysiu!



Regards,
Edwin[/COLOR][/SIZE][/FONT]

---

