---
title: "getting .NET frame work in WINE"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by itachis.eyes on 2009-11-20
well i like to mess around with computers so i'm seeing just how much of windows i can emulate in WINE. 
i found an post  that showed you how to install .NETframework in WINE with the following commands:
```
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts dotnet20
sh winetricks fakeie6
```but every time i get to:
```
sh winetricks corefonts dotnet20
``` it says that sh can't open WINE

i'm not sure where to go from here.

---

### Post by iNaitvad on 2009-11-20
Im sorry if this question is stupid, but did you installed wine?

---

### Post by itachis.eyes on 2009-11-20
> **iNaitvad said:**
> Im sorry if this question is stupid, but did you installed wine?

XD no no, its a very good question. and yes i did install WINE

*off topic* 
you have no idea how many people told me they couldn't boot there computer, so i get to there house and i plug it in and...it works, because it was plugged in, so i understand your reasoning behind that question! XD

---

### Post by Mark Phelps on 2009-11-21
According to the Wine Application Compatibility site, everything in .Net newer than v3 is rated Garage -- meaning, it will NOT work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586")

---

### Post by gradinaruvasile on 2009-11-21
I did test the dotnet stuff and i can confirm that is garbage... nothing ever worked. Go for VirtualBox if u want to test stuff...

---

### Post by itachis.eyes on 2009-11-21
> **Mark Phelps said:**
> According to the Wine Application Compatibility site, everything in .Net newer than v3 is rated Garage -- meaning, it will NOT work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586)

well that would explain things! XD i guess i'll just go with 3.0 and see what i can do with it 
thanks much (^_^)

---

### Post by iNaitvad on 2009-11-21
Some people might kill me for telling you this, but you can try Playonlinux, Wine Doors or Crossover...just in case...Bye

---

