---
title: "I got problems!"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by Gaut on 2007-07-30
I have installed Wine using this guide
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
The installation goes fine.
But when i want to lunch Wine. i cant find it anywhere.
It is not under applications. i have tried to edit the menus and it is not there.
i have tried to install it from the "Add/Remove" Application, but it wont show up.

any ideas where my Wine went?

using Ubuntu Feisty Fawn 7.04

---

### Post by aysiu on 2007-07-30
Wine isn't an independent application. It's a helper application that allows you to launch .exe files.

To launch it from the graphical interface, right-click on the .exe file and select to open it with Wine.

From the terminal, type ```
wine *nameoffile*.exe
```

More details here:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by roachk71 on 2007-07-30
...And don't forget to run 'winecfg' from the terminal before running apps under wine, if you haven't already done so... :)

---

### Post by gobbles414 on 2007-07-30
If installed in Feisty correctly from Synaptic, Wine will leave a couple of launchers in your applications menu. For example, one is for a version of the minesweeper game (as I recall). You should also see winecfg and the wine registry editor in either preferences or administration -- I can't remember exactly. If these aren't visible in the menu editor, then I would suggest doing a COMPLETE REMOVE of Wine in Synaptic. Finally, there is a set of commands that you can run in terminal before a complete remove that will clean some extra wine preferences from your system -- just in case your install was corrupted. I'm sorry that I can't remember the commands, but I seem to remember finding them somewhere in these forums.

P.S. You can always create a launcher for your windows programs in the menu editor. Just enter the launch command as you would in the terminal.

---

