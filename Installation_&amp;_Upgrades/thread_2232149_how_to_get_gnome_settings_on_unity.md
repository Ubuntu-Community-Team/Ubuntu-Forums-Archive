---
title: "how to get gnome settings on unity?"
date: 2014-06-30
forum: Installation &amp; Upgrades
---

### Post by serouj2 on 2014-06-30
any ideas how to get this whatever it is called in unity?

---

### Post by AnotherKevin on 2014-06-30
> **serouj2 said:**
> any ideas how to get this whatever it is called in unity? 
[https://www.google.com.lb/search?q=gnome+blender&es_sm=93&source=lnms&tbm=isch&sa=X&ei=oC6xU4GgGMq60QXU9IC4Bw&ved=0CAgQ_AUoAQ#facrc=_&imgdii=_&imgrc=L73knC7JYOSEDM%253A%3BaqKfz7c31m6VNM%3Bhttp%253A%252F%252Fwiki.blender.org%252Fuploads%252Fc%252Fcd%252FBlender_Manual_-_Installing_Blender_2.5_-_Gnome_Icon_Adding_Picture_4%3Bhttp%253A%252F%252Fwiki.blender.org%252Findex.php%252FFile%253ABlender_Manual_-_Installing_Blender_2.5_-_Gnome_Icon_Adding_Picture_4%3B800%3B600]("http://wiki.blender.org/uploads/c/cd/Blender_Manual_-_Installing_Blender_2.5_-_Gnome_Icon_Adding_Picture_4")


It appears to be an installation pkg for Blender.  It should run under Unity, but to get Gnome, try ```
apt-get install gnome
```.  

I would recommend installing Synaptic to handle installation of packages, especially major changes such as changing Desktop Environments.  It isn't connected to pay type servers and won't break your system and is easy to use. It handles downloads and dependencies and installs them easily.  All you have to do is pick your package.

Kevin

---

### Post by ajgreeny on 2014-06-30
Sorry, but what is it exactly that you want?  You show a picture of the desktop with a menu; is it a menu that you want to add to unity?

---

### Post by serouj2 on 2014-06-30
i already have gnome shell but still it doesnt have that blender thingie

---

### Post by serouj2 on 2014-06-30
yes i want that menu

---

### Post by grahammechanical on 2014-06-30
Folks. Do not click that link. It downloads an image file. Harmless, may be. Bad manners, most certainly. I like to have control over what downloads on to my machine.

---

### Post by serouj2 on 2014-06-30
i have no idea LOL ...all i did was copy and paste the image url ...so is there any way i can get that small menu on my unity?

---

### Post by grumblebum2 on 2014-07-04
In the terminal...
```
sudo apt-get install classicmenu-indicator
```
Search for **classicmenu-indicator** in the dash or run with alt+F2

---

