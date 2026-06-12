---
title: "8xx workaround without xorg.conf"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by mPasCa on 2010-11-05
I'm trying to get my 855gm card working on 10.4. I've had two problems and I was hoping to fix them using this guide: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes). I'm stuck b/c I've no xorg.conf file, only an xorg.conf.failsafe. Here's the lowdown:

Problem 1 [fixed]: Blank screen at startup.
Solution: Use GTT incoherency patch.

Problem 2 [unsolved]: Screen freezes when I close the laptop lid (see also the comment here [http://ubuntuforums.org/showpost.php?p=9187302&postcount=4](http://ubuntuforums.org/showpost.php?p=9187302&postcount=4)). 

So I'm trying workaround F at the wiki link above. I have exactly the correct card---problem is, there I've got no xorg.conf file to edit, only an xorg.conf.failsafe.

Any ideas how to fix this, that is, get a darn xorg.conf file so that I can finish the workaround?

---

### Post by dino99 on 2010-11-05
actual kernel directly deals with X, so no need for xorg.conf (but you can use gedit to "save as" the "failsafe" one as xorg.conf

more info:
[http://www.google.com/search?as_q=855gm%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=855gm%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by mPasCa on 2010-11-05
> **dino99 said:**
> actual kernel directly deals with X, so no need for xorg.conf (but you can use gedit to "save as" the "failsafe" one as xorg.conf

more info:
[http://www.google.com/search?as_q=855gm%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=855gm%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)
Thanks. Any ideas how to complete workaround F in the wiki to force UXA rendering then? I'll assume that copying in a new xorg.conf file won't fix anything if the kernel doesn't look at it. 

Drats!

---

