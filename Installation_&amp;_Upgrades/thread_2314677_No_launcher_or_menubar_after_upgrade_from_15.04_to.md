---
title: "No launcher or menubar after upgrade from 15.04 to 15.10"
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by Edward_Diener on 2016-02-23
I upgraded Ubuntu from 15.04 to 15.10 using the Software Update applications using the Unity desktop manager. Everything occurred without any errors and I rebooted into 15.10. But my 15.10 desktop shows no Launcher along the left side of the window and no menubar on top of the window. The only things I can see are the desktop folders which I had created on my desktop for 15.04.

What has happened ? Are the Launcher and/or Menubar hidden for some reason in 15.10 ? If not, how do I determine why these are not showing ?

I can right-click on the desktop and open a console window from there. I can probably run any program from the console window if I know the name of the program. But no Launcher and no Menubar means I have essentially no user interface.

Any help to determine why the Ubuntu Unity GUI interface is not being displayed on the desktop would be appreciated. The Launcher and menubar, needless to say, were part of the 15.04 Ubuntu Unity UI. The fact that they have disappeared in 15.10 is pretty disconcerting and makes Ubuntu unusable for me. I do have a backup of 15.04 but the fact that I cannot move forward with 15.04 means that going back to that release by restoring my backup is a dead end for me as far as Ubuntu is concerned.

---

### Post by Edward_Diener on 2016-02-23
I tried:

setsid unity
dconf reset -f /org/compiz/

and now the Unity desktop is working again with the Launcher and menubar showing. I found those two lines in a solution in another post and thankfully they work. This is a serious Ubuntu bug, which has been mentioned numerous times in the past, and really needs to be fixed.

---

