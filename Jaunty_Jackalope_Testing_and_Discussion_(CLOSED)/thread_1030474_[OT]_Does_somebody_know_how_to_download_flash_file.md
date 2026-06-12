---
title: "[OT] Does somebody know how to download flash file from web?"
date: 2009-01-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-04
Hi all, 
 Does anybody of a tool or something which tells how to download a flash file out of a website. 

I want to download the flash file which is being shown at 

[http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/index_en.html](http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/index_en.html)

Its a flash file which shows how the recent outages were fixed but don't have the speed to see it online so want to get it and then see it offline.

---

### Post by jfernyhough on 2009-01-04
It's not easy as it's split into a number of elements and requests.

Each of the following provide a different element; whether it's possible to download them all, put them in the same directory, and have it work? No idea.

You could try combining this with a Firefox "Save webpage", put the files in the index_en_files dir and telling Firefox to work offline... it might work...

```

http://www.orange.com/js/hbx.js
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/html/javascript/swfobject.js
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/media/images/plugin.jpg
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/media/videos/chefmission1.flv
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/swf/appLoader.swf?v=1
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/swf/main.swf?v=1
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/swf/rupture.swf?v=1
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/errors.xml?v=1231093859619
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/fin.xml?v=1231093858986
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/fin.xml?v=1231093859121
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/forms.xml?v=1231093859507
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/friend.xml?v=1231093859229
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/home.xml?v=1231093855766
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/main.xml?v=1231093859341
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/recuperation.xml?v=1231093857428
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/recuperation.xml?v=1231093857579
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/remise.xml?v=1231093858514
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/remise.xml?v=1231093858863
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/reparation.xml?v=1231093858199
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/rupture.xml?v=1231093855950
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/rupture.xml?v=1231093856249
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/rupture.xml?v=1231093856710
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_chefmission1.xml?v=1231093860395
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_chefmission2.xml?v=1231093861109
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_denuder.xml?v=1231093861237
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_fin.xml?v=1231093860265
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_lover.xml?v=1231093861347
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_moulage.xml?v=1231093861496
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_radioboite.xml?v=1231093861651
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_recuperation.xml?v=1231093859859
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_recupfocus11.xml?v=1231093860499
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_recupfocus12.xml?v=1231093860622
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_recupfocus21.xml?v=1231093860863
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_recupfocus22.xml?v=1231093860994
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_remise.xml?v=1231093860141
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_reparation.xml?v=1231093860023
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_rupture.xml?v=1231093859752
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/en/subtitles_soudure.xml?v=1231093860748
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/layout.xml?v=1231093861995
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/rubriques.xml?v=1231093855647
http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/xml/videos.xml?v=1231093861828
```

---

### Post by ajgreeny on 2009-01-04
Interesting one.  I tried out of interest doing what I sometimes do with flash, which is letting the whole video load and then just copy the flash file from /tmp folder to home, but there is no flash video showing in tmp, so the file stream must be different to many.  For future, that seems to work very well for many, or even most flash videos, but not all, eg this one and BBC flash iPlayer videos are not downloadable this way.

---

### Post by BwackNinja on 2009-01-04
from jfernyhough's post, 
[http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/media/videos/chefmission1.flv](http://www.orange.com/sirius/dossiers_anim/cables_sous_marins/media/videos/chefmission1.flv) would be the only video out of all of them, so that's the only thing you'd need to download I think. .flv files play in totem, mplayer, vlc, etc.

---

### Post by ShirishAg75 on 2009-01-04
That .flv file doesn't have animation. It has one of the rescue vessels commander saying something in french. Most probably sharing some information about state of things or something like that.

---

### Post by vishalrao on 2009-01-04
tried the FF plugin called "DownThemAll" ? that might work

---

### Post by ShirishAg75 on 2009-01-05
Nope that addon also doesn't work (or I don't know how to use it in a flash enabled page)

---

### Post by alexv75 on 2009-01-05
Try the cacheviewer plugin - sort the files by "Last Fetched" (newest first), see which has the biggest file size (it should be .flv or .swf) and save it...

---

### Post by scaine on 2009-01-05
I think there's another firefox plug-in out there called "FlashGot" or something like that.  Never used it, but it's for lifting flash enabled content and creating a single SWF file out of it - might work here, but I've not used it for ages - don't even know if it's FF3 compatible.

---

