---
title: "Opera 10 beta bad font smoothing"
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yoasif on 2009-06-04
Not sure if this is a Karmic issue, or one with Opera, but I figured I'd ask here for some ideas. 

I just downloaded the [Opera 10 beta]("http://www.opera.com/browser/download/?ver=10.00b1") and on some pages, the fonts are not being smoothed at all - it looks really bad. On other pages (like ubuntuforums), the fonts seem fine. 

Any ideas?

---

### Post by jmmL on 2009-06-04
I'm pretty sure it's because you've got "turbo mode" enabled. Turning it off (click on in the bottom-left) on my system put everything back to normal. Why not anti-aliasing would save bandwidth I've no idea.

---

### Post by ronacc on 2009-06-04
looking at the same /. page , looks ok here on opera 10 beta , took a screenshot , note it looks better in opera than imageviewer .

---

### Post by yoasif on 2009-06-04
> **jmmL said:**
> I'm pretty sure it's because you've got "turbo mode" enabled. Turning it off (click on in the bottom-left) on my system put everything back to normal. Why not anti-aliasing would save bandwidth I've no idea.Nope, turned that off and reloaded... it seems to be a font/QT/KDE issue (I'm running GNOME). 

Some fonts/pages look just fine. It's very odd.

---

### Post by yoasif on 2009-06-05
I just went ahead and played with the font settings in the browser and changed everything from Bitstream Vera to DejaVu, and reloaded, and everything looks good. 

I also ran opera with opera -debugfont before doing that, which also fixed the issue. Not sure which thing fixed it, but it works now, so I'm happy. :)

---

### Post by Zorael on 2009-06-05
> **yoasif said:**
> I just went ahead and played with the font settings in the browser and changed everything from Bitstream Vera to DejaVu, and reloaded, and everything looks good.
So was the first screenshot when using Bitstream Vera? I thought they were just symlinked to eachother nowadays? Compared to that other attachment, I like the sharp look better, would love to get that in Firefox.

> **yoasif said:**
> it seems to be a font/QT/KDE issue (I'm running GNOME).
Always Qt/KDE's fault, isn't it! *twitch* ;3

---

### Post by Eestlane on 2009-06-05
yoasif, try to use qt4 build maybe
[http://ftp.opera.com/pub/opera/linux/1000b1/beta1/en/](http://ftp.opera.com/pub/opera/linux/1000b1/beta1/en/)

---

### Post by glasen on 2009-06-05
I have had the same problem. For me the following solution helped :

1. Only select fonts in Opera, which have "unknown" in their name. All other fonts will have no Anti-Aliasing.

2. This will fix the font hinting in Opera :
```
sudo rm /etc/fonts/conf.d/10-hinting-medium.conf
sudo ln -s /etc/fonts/conf.avail/10-hinting-full.conf /etc/fonts/conf.d/
```

---

### Post by ubername on 2009-06-05
try switching off
opera:config#UserPrefs|EnableCoreXFonts

---

### Post by yoasif on 2009-06-06
> **ubername said:**
> try switching off
opera:config#UserPrefs|EnableCoreXFontsthis was already off (and still is).

---

### Post by durand on 2009-06-07
> **Eestlane said:**
> yoasif, try to use qt4 build maybe
[http://ftp.opera.com/pub/opera/linux/1000b1/beta1/en/](http://ftp.opera.com/pub/opera/linux/1000b1/beta1/en/)

I wonder when they will release a qt4 build for 64bit.

---

