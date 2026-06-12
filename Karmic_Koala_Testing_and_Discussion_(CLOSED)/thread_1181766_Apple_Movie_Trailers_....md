---
title: "Apple Movie Trailers ..."
date: 2009-06-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-06-08
After upgrade from 9.04 to 9.10 today I (my machine ... :) ) lost the ability to watch Apple Movie Trailers ... Any help? Somehow I lost way of using Quick Time...

---

### Post by taavikko on 2009-06-08
> **zika said:**
> After upgrade from 9.04 to 9.10 today I (my machine ... :) ) lost the ability to watch Apple Movie Trailers ... Any help? Somehow I lost way of using Quick Time...

Could be related to fact that quicktime is being upgraded by Apple, due to severe vulnerability. ?

---

### Post by zika on 2009-06-08
> **taavikko said:**
> Could be related to fact that quicktime is being upgraded by Apple, due to severe vulnerability. ?
It might be, any news when it will be resolved and how ... ?

---

### Post by pferraro on 2009-06-08
This looks like an issue with the recently updated totem-mozilla package.  If you check out Firefox->Tools->Addons->Plugins, none of the totem plugins are installed, including the one that handles quicktime files.

---

### Post by taavikko on 2009-06-08
> **pferraro said:**
> This looks like an issue with the recently updated totem-mozilla package.  If you check out Firefox->Tools->Addons->Plugins, none of the totem plugins are installed, including the one that handles quicktime files.

So it seems...
"about : plugins" doesn't show nothing except "java/default/demo print/shockwave"

---

### Post by pferraro on 2009-06-08
> **pferraro said:**
> This looks like an issue with the recently updated totem-mozilla package.  If you check out Firefox->Tools->Addons->Plugins, none of the totem plugins are installed, including the one that handles quicktime files.

If you look at the directory contents of /usr/lib/xulrunner-addons/plugins/, all of the libtotem-*.so sym links are broken.

---

### Post by n4p1 on 2009-06-08
Yep, totem-plugins are broken. Dosent work at all...

---

### Post by artir on 2009-06-08
GOTO Youtube :)

---

### Post by zika on 2009-06-08
> **artir said:**
> GOTO Youtube :)
What? Those "click here for ..." ... ?

---

### Post by syko21 on 2009-06-08
Try using gecko-mediaplayer instead. It's worked for me flawlessly every time.

---

### Post by taavikko on 2009-06-10
Should be fixed by this: [https://bugs.edge.launchpad.net/ubuntu/+source/totem/+bug/385194](https://bugs.edge.launchpad.net/ubuntu/+source/totem/+bug/385194) ?

---

### Post by taavikko on 2009-06-10
> **taavikko said:**
> Should be fixed by this: [https://bugs.edge.launchpad.net/ubuntu/+source/totem/+bug/385194](https://bugs.edge.launchpad.net/ubuntu/+source/totem/+bug/385194) ?

Yep, fix released and working :)

---

### Post by zika on 2009-06-10
> **taavikko said:**
> Yep, fix released and working :)Not here. I still get warning that I should get QuickTime ... ?
Sorry, just now I've seen updates and everything is OK. Thank You!

---

### Post by zika on 2009-06-29
Again no playback on Apple Movie trailers ... :(

---

