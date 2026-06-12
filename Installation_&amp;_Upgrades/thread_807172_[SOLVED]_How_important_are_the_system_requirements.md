---
title: "[SOLVED] How important are the system requirements for a Hardy install?"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by macness on 2008-05-25
I recently was given a A computer [which I'm typing from now] where I *know* of the following specs:

AMD Athlon 800Mhz
128 MB of RAM
60GB HDD

Not really sure what motherboard it has...
Currently it's running Windows but every time I install the Live CD (Ubuntu and Xbuntu) and both just sit at the Hardy Wallpaper.  So then I said, aw heck with this, and tried the Alt Install (Ubuntu) and found that it just halts when reading the HDD.  So thinking it was the HDD, I replaced it - same thing.  Then I thought, "maybe it's the IDE cable" grasping for straws - and replaced that! Then I said, "perhaps the motherboard?" and installed Windows on it.  That actually worked!

I would prefer NOT to use Windows XP on this machine and setup Ubuntu if possible.  Would it be fruitful to try an older version like Dapper (rolling eyes)? Or does anyone else have any suggestions?

:confused:

[edit] FYI, I also have tried using different CD's (which work fine on other computers) and searching relevant posts.

---

### Post by p_quarles on 2008-05-25
The specs on that machine are too low for the live CD and its installer, so that's out. What you can do, however, is use the alternate installation CD, and then select the "command line installation" option from the menu.

This will allow you to install what you need, and not load up everything and the kitchen sink as the default Ubuntu setup does. The following tutorial will show you the basic steps to take, as well as suggest some other options:
[Modest Specs installation](http://www.psychocats.net/ubuntu/minimal)

You should also consider using one of the lighter window managers, as opposed to the standard ones such as Gnome or KDE. Window managers such as Fluxbox, Openbox or IceWM will eat up fewer system resources, and leave more for the applications you want to run.

---

### Post by macness on 2008-05-25
Well I did use the Alt install, but I'll try the command line install to see if that works out.  Thanks for the suggestion.

---

### Post by macness on 2008-05-25
Heh Funny enough, the Hard Drive WAS failing - I guess Ubuntu knew something Windows didn't, a new hard drive (with a bit of coaxing) worked.

Also, I used the Ubuntu Alt Install.

---

