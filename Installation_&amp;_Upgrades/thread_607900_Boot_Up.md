---
title: "Boot Up???"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by tibby_ on 2007-11-09
so i installed ubuntu studio fine on my laptop but then when i reboot my computer after the installation instead of taking me to the login screen or anything it goes through all of these comand prompts and stuff and says ok but then just does nothing after that. so i hit enter and it asked me for my username and password so i did it and it gave me a message that said there is no waranty of any kind for ubuntu and so on and then just gave me another command prompt line. any suggestions, i just wanna log on and have some fun!!!!!!!!

---

### Post by zvacet on 2007-11-09
Maybe it is your graphic card.When you see next command line type

```
sudo dpkg-reconfigure xserver-xorg
```

and select **vesa **driver.That should give you graphic,and after that you can install drivers for your card.

---

### Post by bulldog on 2007-11-09
Did you install the server cd by accident?
Or did you boot the recovery mode.

You can install the desktop [GUI] with aptitude though.
Type in your console```
sudo aptitude install ubuntu-desktop
```

---

