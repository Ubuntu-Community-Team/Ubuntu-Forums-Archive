---
title: "&quot;custom&quot; install cd"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by simple on 2005-05-30
well i want to remove ubuntu for the time being and i am wondering if i can make an install iso that will keep everything exactally like it is, and even certain things i've downloaded..

---

### Post by jasmuz on 2005-05-30
[QUOTE=simple]well i want to remove ubuntu for the time being and i am wondering if i can make an install iso that will keep everything exactally like it is, and even certain things i've downloaded..[/QUOTE]
 None that i know off..but you can back up your cache from the apt pagackages you have downloaded...
They are located in /var/cache/apt/archives
Hope this helps.

---

### Post by bored2k on 2005-05-30
It's not impossible.
[http://www.google.com.do/search?q=ubuntu+remastering&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official](http://www.google.com.do/search?q=ubuntu+remastering&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)

You might as well save your .configs and copy them to a fresh install.

---

### Post by equilibrium on 2005-05-30
could you not do it the gentoo stage4 backup way using chroot etc?

[http://forums.gentoo.org/viewtopic-t-312817.html](http://forums.gentoo.org/viewtopic-t-312817.html)

just tar's up your whole install so you can restore it at a later date. I made one ages ago after spending over 7hrs installing gentoo from stage1 :) had to put it on a dvd tho as it wouldn't fit on a cd

---

### Post by mingus on 2005-05-30
I agree with equilibrium.  Just a note to add if you don't have a DVD burner, I believe you can tar and restore certain directories (or partitions) separately.  This would permit using CD's.  I used a similar technique recommended by SuSE to move /var and /usr and /opt (as I recall), to larger partitions.  I think the principle is the same.

---

### Post by bryanlking on 2005-05-31
Rather than creating an "install CD", you can always boot into Kanotix and run partimage to create a "ghost" type image of your partition.  That way you can always go back and restore it.  It's very easy to use and works very well.

---

