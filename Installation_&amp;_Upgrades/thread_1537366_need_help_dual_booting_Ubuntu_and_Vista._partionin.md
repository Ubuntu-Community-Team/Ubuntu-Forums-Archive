---
title: "need help dual booting Ubuntu and Vista. partioning :/"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by acornty on 2010-07-23
hello so i had a dual boot system before using wubi and that all worked out great. but the fact that the computer cant hibernate is a very large drawback since i use this feature very often. so i think i get the basic concept of dual booting. you shrink your c drive so you can have space for ubuntu. then when installing ubuntu you use that unallocated space. however when i try to shrink my drive it shows that the largest i can shrink it to is 0 mb. does anyone know why this is? i have a 218 gb hardrive with 126 gigs free. I'm on a dell inspiron 1545 32 bit with 3 gigs of ram. please help me! thanks!

---

### Post by rawlins02 on 2010-07-23
See this article and the user comments. I just went through this yesterday. I can't say the defragging was the solution for me, as I seemed to have somehow been able to reduce the Windows C partition from about 400GB down to 80 by reducing in small chunks.  But from what was written in this article there are often unmovable files that prevent the resizing. Hope this helps:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by Megaptera on 2010-07-23
On my Dell there was a separate recovery partition (D) with Vista on C. As I have the Dell recovery discs, I deleted D (20gb or so) and installed Ubuntu there. Has been working fine for about a year now.

Could you do something similar? 

I can access My Docs (etc) on Vista fro Ubuntu so I backup everything there & still have a working Vista.

---

### Post by penguinjockey on 2010-07-23
i run a dual boot with windows 7 (please dont tell anyone...its embarrassing) and Ubuntu 10.04 ive had to reinstall both, to put it mildly a few times because i keep frakking my system because i experiment too much. but the best way i have found that IS stable is to install thw windows first and then to install the linux next and to either let ubuntu automatically partition evenly or to use the gra[phical partitioner slidebar

---

### Post by acornty on 2010-07-23
> **rawlins02 said:**
> See this article and the user comments. I just went through this yesterday. I can't say the defragging was the solution for me, as I seemed to have somehow been able to reduce the Windows C partition from about 400GB down to 80 by reducing in small chunks.  But from what was written in this article there are often unmovable files that prevent the resizing. Hope this helps:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
thanks but it tells me to delete the hibernation file and disable system restore points which in my eyes is kinds dumb lol even though it says i can get them back. and the worst part is I'm sure doing these things would make it work. I'll have to think about it. thanks!
EDIT: well i dont know if i wanna delete my recovery drive lol, but that is a pretty good idea. :) besides my recovery drive is only 15 gigs and i wanted at least 20 for my ubuntu side.
EDIT 2: i went with rawlins idea and it worked like a charm thanks!

---

