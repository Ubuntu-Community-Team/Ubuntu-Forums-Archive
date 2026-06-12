---
title: "Jaunty Update Error"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kamssada on 2009-03-31
I just updated my system to jaunty using the 

update-manager -d. 

Update was successful, no errors. After reboot, i'm not able to use computer, because a series of nautilus windows start popping and fill up my taskbar. And my computer eventually crashes after that. 

I was wondering if that wasn't because of some autostart item i got. I unistalled using ctrl alt F1 all the softwares that i could possibly think of that might cause such an error, things like xmbc, miro, picasa, googleearth, cairodock... 

Please help

---

### Post by biji on 2009-03-31
try to create new user and login using that user

---

### Post by drs305 on 2009-03-31
It is a known bug. First, open a terminal with ALT-F2 or via the menu if you can. Enter "killall nautilus" and "killall gnome-panel" repeatedly until nautilus stops spawning. Eventually nautilus will stop filling up the Window List panel. Note: There may be better ways to do it but this procedure *should* stop it before your computer crashes. You can use the up arrow in terminal to bring up a previous command.

Once you have the spawning stopped:
```
gksudo gedit /usr/share/applications/nautilus.desktop

```
Change:
```
X-GNOME-AutoRestart=[COLOR="DarkRed"]**true**[/COLOR] 
*to:*
X-GNOME-AutoRestart=[COLOR="DarkRed"]**false**[/COLOR]
```
Save the file.

---

