---
title: "Any fonts news?"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 6205 on 2010-02-21
What about fonts? Is default fontconfig somehow different or improved in Lucid? Current Karmic defaults are Sans 10 with subpixel hinting. They are not bad, but not good either. 

Look at fonts on these pictures, they seems to me different, like default Sans 10 bud slightly improved, sharper, thinner...
[http://www.starryhope.com/linux/ubuntu/2010/ubuntu-switches-to-yahoo-search-kinda/](http://www.starryhope.com/linux/ubuntu/2010/ubuntu-switches-to-yahoo-search-kinda/)

---

### Post by Digital Hick on 2010-02-21
Last time I checked Liberation Serif was default now in OO3.2 on Lucid.  That was different.:popcorn:

---

### Post by psyke83 on 2010-02-21
> **6205 said:**
> What about fonts? Is default fontconfig somehow different or improved in Lucid? Current Karmic defaults are Sans 10 with subpixel hinting. They are not bad, but not good either. 

Look at fonts on these pictures, they seems to me different, like default Sans 10 bud slightly improved, sharper, thinner...
[http://www.starryhope.com/linux/ubuntu/2010/ubuntu-switches-to-yahoo-search-kinda/](http://www.starryhope.com/linux/ubuntu/2010/ubuntu-switches-to-yahoo-search-kinda/)

The fonts in that screenshot are different, because Firefox is currently using an internal version of cairo which does not support the improved FIR filtering algorithm. It's filed as [bug #512615]("https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/512615").

The rest of the system uses identical font rendering to Karmic, as will Firefox when the bug is fixed.

By the way, what kind of monitor do you have? The fonts in that screenshot look terrible on both my screens (a TFT monitor and LCD laptop screen - you can see a lot of colour fringing).

---

### Post by 6205 on 2010-02-22
IMO default Sans 10 with subpixel hinting have nice shape, but they are too bol to my tastes. If they only were little thinner.
Also they are somehow misplaced, like they are too much up, instead of centered. If you change font to Droid Sans 11 with same hinting, you will get the same font desing and size, but you will notice that they will move a few pixels to bottom and will not be somehow misplaced, upper oriented. But they are still too bold. On that screenshot were those Firefox fonts somehow sharper, thinner i think...

BTW i have HP w2007v, nothing special. But if you give me some hints how to get fonts like this in Ubuntu [http://www.abclinuxu.cz/images/screenshots/4/7/151474-salutis-desktop-20849.png](http://www.abclinuxu.cz/images/screenshots/4/7/151474-salutis-desktop-20849.png) i would really appreciate that :)

---

### Post by pferraro on 2010-02-22
> **6205 said:**
> IMO default Sans 10 with subpixel hinting have nice shape, but they are too bol to my tastes. If they only were little thinner.
Also they are somehow misplaced, like they are too much up, instead of centered. If you change font to Droid Sans 11 with same hinting, you will get the same font desing and size, but you will notice that they will move a few pixels to bottom and will not be somehow misplaced, upper oriented. But they are still too bold. On that screenshot were those Firefox fonts somehow sharper, thinner i think...

BTW i have HP w2007v, nothing special. But if you give me some hints how to get fonts like this in Ubuntu [http://www.abclinuxu.cz/images/screenshots/4/7/151474-salutis-desktop-20849.png](http://www.abclinuxu.cz/images/screenshots/4/7/151474-salutis-desktop-20849.png) i would really appreciate that :)

If it's thin fonts you want, increase the hinting to Medium or Full (the ubuntu default is Slight).  I use Droid Sans as well, since it renders much more compactly than the DejaVu equivalent.

---

