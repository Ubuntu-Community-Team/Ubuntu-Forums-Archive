---
title: "where do new apps get stored and ..."
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by mangurian on 2007-12-05
[SIZE="4"]question 1:
I installed gparted and was able to find it via search, but could not figure out how to get it listed in my application menu.  Is there a way to do that?

question 2:
I installed a newsreader called "hellanzp" and I can't find it anywhere.  Thinking that perhaps the istall had failed, I went back to the package installer and tried to install it again.  It came up as a reinstall, so Ubuntu knows I have it.  Any advice on how to find it ?[/SIZE]

---

### Post by mikewhatever on 2007-12-05
Hi there, did you know, we are not blind. Now to your questions. 
When you install gparted, it should appear under System>Admin as Gnome Partitions Manager. Do no look for Gparted in the menus.

To find where some program is installed, say, hellanzp, run the following commands
> sudo updatedb
locate hellanzp

You'll be presented with a list of directories. To simply locate an executable for launching the program, use <which hellanzp>, however, if the installations failed, it probably would not be working. Under normal circumstances, most programs can be started by hitting alt+f2 and typing the program's name.

---

