---
title: "Uninstall Winemine"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Vexiphne on 2007-04-24
Does anyone know how I can remove that annoying little game called winemine?
I've looked for it in Add/Remove Applications and in the package manager, but it's no where to be found.

---

### Post by dannyboy79 on 2007-04-24
i don't know what this game is but I can still try to help you. is it a game you run under wine? (wine is a windows emulation layer for running windows programs within linux) If not than simply try this

sudo aptitude remove winemine

if that doesn't work, then it might be part of the metapackage, gnome-desktop. you could always just use this

sudo find / -name *mine*

to find every location that you find winemine and delete them. this is obviously a very bad way to do it.

why do you want to get rid ot it so bad.

if it is a windows app, and you installed it thru wine, you need to run it's uninstaller thru wine. so it would something like this

sudo wine ~/.wine/drive_c/Program\ Files/winemine/uninstaller.exe
(Note: you will need to browse the winemine install folder within your username's home dir then in .wine, then in Program Files, then where the game was installed. Let me know and good luck

---

### Post by blitzer on 2007-04-24
Hi Vexiphne,

You can right click on Applications then edit and un-tick the box next to the game to hide it.  Might be good enough :lolflag:

---

### Post by Vexiphne on 2007-04-24
Hi dannyboy79 and blitzer.

The game Winemine was installed when I installed Ubuntu 7.04. Wine was not installed so it couldn't use that.
I've been looking all over for this game so I could remove it, but I just can't find. It It's sooo strange :(
But thanx anyway for you suggestions :)


blitzer: If you read everything I wrote. You would see that I have already tried that :rolleyes:
The game is NOT there.

---

### Post by dannyboy79 on 2007-04-24
did you try to use the find command i suggested????
if it's not in your menu, why do you want to remove it so badly for? just delete it using
sudo rm winemine
after you find it using the search command. if that one didn't work, try it with a different search criteria

sudo find / -name *wine*

---

### Post by blitzer on 2007-04-25
> **Vexiphne said:**
> Hi dannyboy79 and blitzer.

The game Winemine was installed when I installed Ubuntu 7.04. Wine was not installed so it couldn't use that.
I've been looking all over for this game so I could remove it, but I just can't find. It It's sooo strange :(
But thanx anyway for you suggestions :)


blitzer: If you read everything I wrote. You would see that I have already tried that :rolleyes:
The game is NOT there.

:confused:   When I [COLOR="Red"]RIGHT CLICK[/COLOR] Applications an choose edit then click on games to the left - - it is there with a tick box.

---

### Post by dannyboy79 on 2007-04-25
> **blitzer said:**
> :confused:   When I [COLOR="Red"]RIGHT CLICK[/COLOR] Applications an choose edit then click on games to the left - - it is there with a tick box.

yeah, but he may have tried deleting just the file which is why it may not be showing up in applications anymore. I'm not saying he did, I am merely speculating possibly why it isn't showing up there on his machine.

---

### Post by blitzer on 2007-04-25
I bet your right on the money with that problem dannyboy79  :lolflag:

---

### Post by port on 2007-07-26
This was annoying me too. I found it by doing
```

whereis winemine

```
it was found in /opt/picasa/wine/bin/winemine, /opt/picasa/wine/lib/wine/winemine.exe.so, /usr/share/applications/wine-winemine.desktop

i removed those and then clicked on games in menu editor , right clicked on winemine and selected delete.

---

