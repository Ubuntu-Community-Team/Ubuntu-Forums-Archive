---
title: "is installing enough?"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by Eustace Scrubb on 2007-10-01
Warning - total linux noob

I've installed Feisty Fawn, and it runs.  I wanted to learn how to install apps, so I've installed 7zip using Add/Remove, and a game called Amphetamine using the Synaptic package installer.  Neither of these programs have been added to the desktop or to the Applications menu.  How do I run installed programs?

---

### Post by snickers295 on 2007-10-01
> **is installing enough?**
         Warning - total linux noob

I've installed Feisty Fawn, and it runs. I wanted to learn how to install apps, so I've installed 7zip using Add/Remove, and a game called Amphetamine using the Synaptic package installer. Neither of these programs have been added to the desktop or to the Applications menu. How do I run installed programs?If they aren't in the menus then that means they are command-line programs.
go into Applications>Accessories>Terminal  and type:> man 7z then do what the terminal says.  for Amphetamine type: > Amphetamine 

---

### Post by brownknight on 2007-10-01
It if is a game, it should show up in the menu list of games. If it is not there, you can try to locate where the file is using the terminal and type

locate <filename>

This will give you an idea where the program was installed.  The last resort I do is to type the name in the terminal and it launches the program.

---

