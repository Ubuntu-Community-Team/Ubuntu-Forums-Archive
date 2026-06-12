---
title: "pretty new to Hardy, installed updates yesterday - desktop menus GONE"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by ardensdrunk on 2008-06-24
I installed some updates that popped up on the "update" icon on the original panel/main start bar that loads to the top of the screen by default.
Once i restarted after being asked i have no desktop menu's anymore

compiz still works technically as windows minimize i still get the affects... my cube also still works ..

i just dont have the menu up top.

i assume it something that was part of the recent upgrades that i ran, but i cant figure it out.
i have a raedeon 9800 pro using the restricted drivers... had no issues up to this point.

the only way i was able to get to a browser to post this was to create a new document on the desktop using right click and name it *.html so i could open firefox.

any ideas?
are there commands i can run via the terminal (alt + f1-f6) that will show the most recent updates and or is there a command i can use to remove the most recent updates?

i really dont want to have to boot into XP just to be able to use my computer... hardy was working GREAT up until those updates i installed.


thanks in advance!!

---

### Post by iaculallad on 2008-06-24
If it's just the menu and not the ENTIRE panel that's missing: Try to right-click on your top menu bar, select "Add to Panel" then select/click "Menu Bar" from "Utilities" and click on "Add". Click on close and that should return your Ubuntu menu.

---

### Post by ardensdrunk on 2008-06-24
> **iaculallad said:**
> If it's just the menu and not the ENTIRE panel that's missing: Try to right-click on your top menu bar, select "Add to Panel" then select/click "Menu Bar" from "Utilities" and click on "Add". Click on close and that should return your Ubuntu menu.

the WHOLE panel is gone ... by panel i of course mean what houses the clock, shortcuts to firefox etc ...

i've tried right clicking where the panel USED to be, but i get the same options that you would clicking anywhere else on the desktop

its weird ...

---

### Post by iaculallad on 2008-06-24
If pressing Alt+F2 could bring you the "Run Application" window, type "gnome-terminal" (w/o quote) and input **gnome-terminal** and press Enter Key to open your terminal then issue the commands below:

If pressing Alt+F2 does not pop the "Run Application" window, press Ctrl+Alt+F1 then issue the commands below:

```
gnome-session-remove gnome-panel
gconftool-2 –recursive-unset /apps/panel
gnome-panel &
```

Ctrl+Alt+F7 again to log back in to your GUI. Logout on your account and log back in.

---

### Post by ardensdrunk on 2008-06-24
> **iaculallad said:**
> If pressing Alt+F2 could bring you the "Run Application" window, type "gnome-terminal" (w/o quote) and input **gnome-terminal** and press Enter Key to open your terminal then issue the commands below:

If pressing Alt+F2 does not pop the "Run Application" window, press Ctrl+Alt+F1 then issue the commands below:

```
gnome-session-remove gnome-panel
gconftool-2 –recursive-unset /apps/panel
gnome-panel &
```

Ctrl+Alt+F7 again to log back in to your GUI. Logout on your account and log back in.



tried the first two commands but they didnt work.
i got "cannot open display" when i ran the first command

and then i got command not found on the second one.

---

### Post by iaculallad on 2008-06-24
> **ardensdrunk said:**
> tried the first two commands but they didnt work.
i got "cannot open display" when i ran the first command

and then i got command not found on the second one.

As for the second command, gconftool-2 –recursive-unset /apps/panel, it should be **gconftool-2 --recursive-unset /apps/panel**.

What about issuing the command:

```
sudo debconf gnome-panel
```

---

### Post by ardensdrunk on 2008-06-24
> **iaculallad said:**
> As for the second command, gconftool-2 –recursive-unset /apps/panel, it should be **gconftool-2 --recursive-unset /apps/panel**.

What about issuing the command:

```
sudo debconf gnome-panel
```

when issuing the above command it states that it cannot exec "genome-panel"
it also says something about not being able to find it.

---

### Post by iaculallad on 2008-06-24
> **ardensdrunk said:**
> when issuing the above command it states that it cannot exec "genome-panel"
it also says something about not being able to find it.

That would be **gnome-panel** in **sudo debconf gnome-panel**.

---

### Post by ardensdrunk on 2008-06-24
> **iaculallad said:**
> That would be **gnome-panel** in **sudo debconf gnome-panel**.

haha
yeah i got that wrong

however when i do type it it still says command not found

it also mentions that gnome-panel is not installed and gives me a apt-get statement to download it.

did those updates remove gnome-panel?  and if so is it as easy as re-installing it to get it back?

---

### Post by iaculallad on 2008-06-24
> **ardensdrunk said:**
> haha
yeah i got that wrong

however when i do type it it still says command not found

it also mentions that gnome-panel is not installed and gives me a apt-get statement to download it.

did those updates remove gnome-panel?  and if so is it as easy as re-installing it to get it back?

That might be the case, try to install the gnome-panel.

---

### Post by ardensdrunk on 2008-06-24
> **iaculallad said:**
> That might be the case, try to install the gnome-panel.



well that did it!
i reinstalled gnome-panel and now i have my bar again.

when it came back up it mentioned something about a mixer applet and trash applet having issues .. it asked me to delete them so i did ....

now the software update icon is there again ..

i wander if i should update again... hrm
kinda scared to know ..


thanks man i really appreciate your help!

---

