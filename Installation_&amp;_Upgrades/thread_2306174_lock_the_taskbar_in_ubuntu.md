---
title: "lock the taskbar in ubuntu"
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by weirdygeekpsych on 2015-12-12
I am new to Ubuntu, my question is whenever I hover the mouse pointer on top of window it shows file menu.  But I want that to be static, I mean without hovering the mouse pointer I need to access the file menus?  

 Is there any possible way to do that? 

 Hoping for an good solution

---

### Post by scoutchorton on 2015-12-12
Hello and welcome to Ubuntu! I tried to make this easier for someone who is new, but you will be getting into the Terminal. Don't worry, you don't need to really understand it, but you should be fine.

Step 1:
Click on the Dash (or use the Windows key if you use that keyboard (don't discriminate against Macs!))
[ATTACH=CONFIG]266111[/ATTACH]

Step 2:
Search Terminal and click on it
[ATTACH=CONFIG]266113[/ATTACH]

Step 3:
Type in the following command (or copy and right click in Terminal to select paste because Ctrl+v doesn't work) and press Enter:
```
gsettings set com.canonical.Unity always-show-menus true
```
To change it back, change true to false
[ATTACH=CONFIG]266117[/ATTACH]

And that's it!

I found the command at [AskUbuntu]("http://askubuntu.com/questions/25785/can-auto-hide-for-the-application-menu-be-turned-off-in-unity") by doing a quick Google search. So don't crown me genius, just a messenger who simplifies things.

If this was too simple, I'm sorry. But anyways, hope you enjoy! :D

---

