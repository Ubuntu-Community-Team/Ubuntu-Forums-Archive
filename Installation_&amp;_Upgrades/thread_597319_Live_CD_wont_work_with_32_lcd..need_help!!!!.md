---
title: "Live CD wont work with 32 lcd..need help!!!!"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by 9to9 on 2007-10-30
ok guys, as subject, but first iam new with ubuntu and linux..so the stories like this..
i have kubuntu 6.10, and ubuntu 7.10, every time iam booting it and choose the option start or install kubuntu/ubuntu, the graphical interface doesnt show up, and iam always back to dos-like menu, i have search internet and try code sudo aptitude install kubuntu/ubuntu-desktop and it doesnt work and install the GUI!!!..i need urs advice huhuhuhuhu..my vga hardware 8600gt nvidia and my display lcd tv 32 inchi lg...

---

### Post by mikewhatever on 2007-10-30
A live cd would load the gui without any installation if the hardware is supported. In your case, the screen is very large. What's the resolution it uses? You can try 

> sudo nano /etc/X11/xorg.conf

and add the required resolution manually. Then Ctrl+o to save and Ctrl+x to exit.

That done, try:

> sudo startx

Lastly, do you get any error messages?

---

