---
title: "Installing and Calling Pinta"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2013-03-28
I was able to install Pinta by using the terminal command
sudo apt-get install pinta*

But it does not show up in my Applications/Graphics window and I don't know how to start it.  I can't even find it if I do a search on the file system.  Can someone help?

---

### Post by Frogs Hair on 2013-03-28
The Pinta icon shows up under the graphics category in unity and also in the main menu/alacarte used in classic and the shell. Perhaps Pinta didn't install correctly.

---

### Post by oldefoxx on 2013-03-28
I'm running Ubuntu 10.04 (I tried 12.04, then went back).  The install process seemed to go fine, though I had to use apt-get instead of the other means since pinta was not given as a choice with them.  I searched the main menu and can't find it.  I don't know what you mean by Unity or alacart.  Must be something else I need to do.  Any more ideas out there?

And something else.  Though I see other choices I can include under Main Menu, I cannot actually add or delete any of them from my menus.  I tried setting them a couple of times, but no effect.  I even tried rebooting and still they came up as they were initially set.  If I can't change my menus, I probaby can't get pinta to display even if it installed correctly.

---

### Post by Frogs Hair on 2013-03-28
I didn't know you were using 10.04 so Unity is not applicable.  Alacate is  the package  that include the main menu  and if Pinta not appearing there it may not have installed properly. If the package didn't configure try the following . ```
sudo dpkg --configure -a
``` ```
sudo apt-get update
```

 If the main menu works after that reinstall Pinta. If the main menu is still not working try reinstalling it  or alacrarte  what ever appears in synaptic. The package is named alacarte on the newer version. 10.04 reaches end of life at the end of April

---

### Post by oldefoxx on 2013-03-28
Synaptic shows alacarte installed.  I flagged to to be reinstalled and then applied that.  After that was done I tried to add more games under the Games menu and removing one.  Again, no change.  It's not working.

---

