---
title: "Dual boot Ubuntu and Vista, Seperate drives, grub settings?"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by tgm4883 on 2007-03-27
I know its on here somewhere, I saw it before, just cant find it now.

I have two seperate drives, one has ubuntu, one has vista.  I followed advice from these forums of only having one drive plugged in while installing, then switching.  I can boot to either vista or ubuntu by pressing F12 and selecting which drive I want to boot from.  The default is the ubuntu drive and has grub installed.  I want to edit grub so I have a vista option there (currently there is no vista option, and I don't want to have to keep pressing f12).  What do I do to grub to change this?

---

### Post by Jose Catre-Vandis on 2007-03-27
```
sudo gedit /boot/grub/menu.lst
```

add this to the bottom of the file:

```
title           Windows Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

replacing (hd0,0) with whatever your 2nd hard drive is, probably (hd1,0) which means (second hard drive, first partition), depends what your cdrom device gets called.

This should do it

---

### Post by tgm4883 on 2007-03-27
I may have to play with it alittle, I should have explained this in my first post.  My first drive (with ubuntu) is a sata drive, then i have 1 ide cable with both my master (vista) and my dvd drive (slave)

:EDIT:

I should also add that when booting, the vista drive is on channel 4

---

### Post by tgm4883 on 2007-03-27
I should have just listened to you the first time instead of thinking "hey, its on channel 4 so i should do (hd4,0).  That didn't work, but as soon as I did (hd1,0) it booted into vista. 

Thanks for help :)

---

### Post by ssican on 2007-03-28
See this Treads: 1)Dualboot Two Hard Drives [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
2)Trying to Dual Boot, using two HD's  [http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)
3)Ubuntu + Vista +Grub or EasyBCD boot problem  [http://www.ubuntuforums.org/showthread.php?t=391194](http://www.ubuntuforums.org/showthread.php?t=391194)
EDIT: 4)Dual Boot Vista and Linux (2 Hard Drives)  [http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux)

---

### Post by Jose Catre-Vandis on 2007-03-28
great :-)

---

