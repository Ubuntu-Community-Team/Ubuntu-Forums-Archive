---
title: "How to remove bottom menu on lubuntu install menu?"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by montyp2 on 2013-09-20
I would like to tweak the lubuntu 13.04 install menu by removing the F1 to F6 function key menu at the bottom.  

I attached an image of the boot install menu I am referring to.

[ATTACH=CONFIG]246376[/ATTACH]


In researching this, I believe this menu is coming from vesamenu.c32, but honestly, not 100% sure on that.  That said, I have not been able to find any configuration files that remove these function key options.  This [link]("http://www.syslinux.org/wiki/index.php/Comboot/menu.c32") has a lot of the configs for menu.c32, but struggling to find anything on vesamenu.c32.  I do prefer the vesamenu.c32 look over the menu.c32 look so I ideally would like to stick using vesamenu.c32.

Is there an easy way of hiding or removing this menu or is it a matter of getting the vesamenu.c32 source code and modifying the c code?

If it is a matter of modifying source code, does anyone know what exact version of isolinux lubuntu 13.04 is using?

---

### Post by Quackers on 2013-09-20
Welcome to UF.
I can't imagine why you would want to do that.
If you managed to remove it and then tried to boot it on a different computer that needs (for instance) the nomodeset boot option to boot, you won't be able to choose it.
That being said I don't know how you would go about doing what you want.

---

### Post by montyp2 on 2013-09-20
Thanks for the welcome.
The main reason why I want to do it is that we have a specific hw model of computer we are using so if it works on one, it works on all type of thing.  I just don't want some users to mess about with these options.  It's amazing how many questions my users come up with about what they are for, etc etc and I don't want to mess with all that.  And saying, just ignore them and move on is often ignored it seems.  :-)  So, no see, no questions, happier me.

---

### Post by Quackers on 2013-09-20
Lol, understood.
Just tell them that they are boot options for other types of system that require different kernel parameters!
Sorry, I just don't know the answer. Maybe someone else will come up with something :-)

---

### Post by sudodus on 2013-09-20
> **montyp2 said:**
> Thanks for the welcome.
The main reason why I want to do it is that we have a specific hw model of computer we are using so if it works on one, it works on all type of thing.  I just don't want some users to mess about with these options.  It's amazing how many questions my users come up with about what they are for, etc etc and I don't want to mess with all that.  And saying, just ignore them and move on is often ignored it seems.  :-)  So, no see, no questions, happier me.

Try the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") if it is going to be an Ubuntu only system: Make a tarball of your system, and then install from that tarball to the other computers. That will be quite easy, and very few questions.

If the systems are 'exactly the same, also the same size of HDD', you can make an cloned image of the drive with [Clonezilla]("http://clonezilla.org/"), and then clone from that to the other computers.

---

### Post by montyp2 on 2013-09-20
Thanks for the pointers, sudodus.  Those do look like some intriguing options.  will definitely check them out.

---

