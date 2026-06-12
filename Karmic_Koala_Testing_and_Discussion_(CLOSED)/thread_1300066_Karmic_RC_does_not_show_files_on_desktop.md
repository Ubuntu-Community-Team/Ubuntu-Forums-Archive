---
title: "Karmic RC does not show files on desktop"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Dangger on 2009-10-24
**See further comments for solution.**


I  just upgraded and the problems are slowly appearing. One of them is that I can't see files on the desktop and if they show they don't refresh:

[[IMG]http://imgur.com/6OTuJs.png[/IMG]](http://imgur.com/6OTuJ.png)

Hiting F5 while on desktop removes them until I open the desktop from the home directory.

---

### Post by ranch hand on 2009-10-24
Don't hit F5.

That sounds like the answer to me.

---

### Post by 101011010010 on 2009-10-24
Hello there,
I just answered this post [http://ubuntuforums.org/showthread.php?t=1300064](http://ubuntuforums.org/showthread.php?t=1300064)
It might help you as well.
I hope it helps.

---

### Post by Dangger on 2009-10-24
Thanks to all I have discovered where the problem was. 

Something happened during the upgrade. Ubuntu Tweak has an option to change the default folder locations. Apparently two folders had the same path, both Downloads and Desktop directed to the path where Desktop is located (/home/usename/Desktop). I redirected each directory to its own path, rebooted and it's all good!

---

