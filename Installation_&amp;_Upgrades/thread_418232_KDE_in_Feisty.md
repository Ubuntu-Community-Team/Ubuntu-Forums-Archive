---
title: "KDE in Feisty?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-04-22
I just installed 7.04 Feisty and so far I like it but HOW do I install the KDE environment?  I'm hesitant to use instructions that apply to Edgy or Dapper.  I don't see it in package manager.

Is there a how to page for Feisty like there is for the earlier versions?

Thanks,

---

### Post by tkjacobsen on 2007-04-22
If you do a
sudo apt-get install kubuntu-desktop
you will get a complete kde environment..

But if you would like to only use kde and not gnome you should probably just install kubuntu.

---

### Post by panty31772 on 2007-04-22
Usually I just use synaptic to install different desktops . 
Though I think this method will work also  , havent tried it myself yet ( attached screenshot of synaptic showing kde )

Open up a terminal:
[COLOR="Blue"]```
sudo aptitude update
```[/COLOR]

Once you've updated, go ahead and install KDE:
[COLOR="Blue"]```
sudo aptitude install kubuntu-desktop
```[/COLOR]

If you want a lighter-weight version of KDE, do :
[COLOR="Blue"]```
sudo aptitude install kde-core
```[/COLOR]


Hope this helps you !!

---

### Post by ascus4 on 2007-04-22
I found it.  This is the page I was looking for.  This is a great site.

[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_KDE](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_KDE)

I didn't see KDE in synaptic so I sodo'd it.  I'm just about to log out and switch over.

---

### Post by ascus4 on 2007-04-22
Ok, it's all  good.

Thanks guys.

---

