---
title: "wine 3d games?"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by maphilli14 on 2009-03-19
I'm running Jaunty on a Lenovo T60p with the opensource drivers.
All 3D functions work fine including compiz.

[IMG]http://lh4.ggpht.com/_tyzfsKXhQs4/ScKJiTXkiDI/AAAAAAAAG8c/eUXeEU5Mqsc/s912/halo-errors.png[/IMG]

[http://picasaweb.google.com/maphilli14/Community#5314961732658300978]("http://picasaweb.google.com/maphilli14/Community#5314961732658300978")

I see the attached artifacts when running Halo: Combat Evolved (version 1, original one) in wine 1.0.1 (jaunty packaged version)

The artifacts you see are present regardless of safe mode or video selections via cli.  I cannot see anything and the cpu runs up to 100%.  I cannot interact with any of the menus and usually have to force quit the game / wine window.

I followed the tutorial on the Wine AppDB as closely as I could and am wondering if someone knows what else I could try.

TIA,

Mike

---

### Post by Woody1987 on 2009-03-19
What graphics card are you using? Also try installing the latest intrepid ibex version of wine from the website, since they dont have jaunty packages yet. And also turn off compiz if your running wine, sometimes it interferes.

---

### Post by maphilli14 on 2009-03-19
Smoking man.... gotta love it!

Vid card
```
lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250]

```

Wine as in this doesn't work:
```

# deb http://wine.budgetdedicated.com/apt jaunty main
# deb-src http://wine.budgetdedicated.com/apt jaunty main

```

but this would?
```

# deb http://wine.budgetdedicated.com/apt intrepid main
# deb-src http://wine.budgetdedicated.com/apt intrepid main

```

---

### Post by Woody1987 on 2009-03-19
for wine go here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

no need to change the repositories.

Your card, i think i have bad news for you, amd no longer support that card in their drivers which means that the official driver from them will not work for you in jaunty, which means that you will have to use the opensource drivers which dont give the performance that the closed sourced ones give, which might be another reason as to why your game isnt working correctly. Mind you i could be wrong, i know they no longer support radeon cards below the 2000 series and according to wikipedia your card is based off an x1600 which is not supported.

---

### Post by ubu-for on 2009-03-19
> **Woody1987 said:**
> Your card, i think i have bad news for you, amd no longer support that card in their drivers which means that the official driver from them will not work for you in jaunty, which means that you will have to use the opensource drivers which dont give the performance that the closed sourced ones give, which might be another reason as to why your game isnt working correctly.
In the past I had several problems with Wine and Compiz, so I had to turn off the 3D desktop in order to play games.

Maybe it's only a problem with Compiz but Woody is probably right. Some notebook users said that another driver called "radeon" or radeonhd" already exists as an alternative for "ati". The Fedora 10 package is called "xorg-x11-drv-radeonhd".

[http://translate.google.de/translate?prev=hp&hl=de&u=http%3A%2F%2Fwww.fedoraforum.de%2Fviewtopic.php%3Ff%3D7%26t%3D16771&sl=de&tl=en](http://translate.google.de/translate?prev=hp&hl=de&u=http%3A%2F%2Fwww.fedoraforum.de%2Fviewtopic.php%3Ff%3D7%26t%3D16771&sl=de&tl=en)

[http://ubuntuforums.org/showthread.php?t=767361](http://ubuntuforums.org/showthread.php?t=767361)

---

### Post by maphilli14 on 2009-03-19
Yes, the laptop/video card is old, but ATI had the right drivers under WinXP (since removed from the dualboot on this machine in favor of Jaunty) and all was well.

What's got me concerned is this error, where Halo thinks it's running on Nvidia... I don't think you can set the vid card in Halo.

[IMG]http://lh3.ggpht.com/_tyzfsKXhQs4/ScKZoQwXA8I/AAAAAAAAG8w/mTOuYBkac5E/Screenshot-Default%20-%20Wine%20desktop.png[/IMG]
[http://picasaweb.google.com/maphilli14/Community#5314979427222225858]("http://picasaweb.google.com/maphilli14/Community#5314979427222225858")

All the directx stuff tests out fine in wine....

Mike

---

### Post by maphilli14 on 2009-03-19
3d perf via glxgears:

```
glxgears 
9307 frames in 5.0 seconds = 1861.314 FPS
9581 frames in 5.0 seconds = 1916.083 FPS
9384 frames in 5.0 seconds = 1876.661 FPS
9746 frames in 5.0 seconds = 1949.184 FPS
9811 frames in 5.0 seconds = 1962.053 FPS

```

---

### Post by Woody1987 on 2009-03-19
try running the game from the terminal and paste the output here

---

