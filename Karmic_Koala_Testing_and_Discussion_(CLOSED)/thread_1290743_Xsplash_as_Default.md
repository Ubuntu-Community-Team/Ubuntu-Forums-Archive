---
title: "Xsplash as Default?"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MTGap on 2009-10-13
Based on the wiki : "* Graphical boot splash that will be running on top of X-server, not Usplash"

But it seems to me that I'm still using usplash and xsplash isn't even installed. Shouldn't it have come with Karmic? I downloaded Alpha 6 and did a fresh install from that. What should I do? Install xsplash?

---

### Post by 23meg on 2009-10-13
It's normal that USplash will be installed, since it's still used, but not normal that you don't have XSplash. You may have inadvertently removed it due to a partial upgrade or other error. Try reinstalling it, and if it turns out other core packages have been removed too, consider doing a fresh install with the beta or a recent daily build.

---

### Post by Longinus00 on 2009-10-13
Kubuntu is not currently using xsplash. Last I heard they were going to use ksplash in the same way as ubuntu uses xsplash.

---

### Post by MTGap on 2009-10-14
Really? Should I be installing KSplash then?

---

### Post by Longinus00 on 2009-10-14
Ksplash should be installed by default?

---

### Post by MTGap on 2009-10-14
I can't even find a package ksplash or anything similar, are you sure about this info?

---

### Post by Longinus00 on 2009-10-14
I meant to say ksplashx instead of ksplash, sorry if that caused some confusion.

[https://wiki.kubuntu.org/KubuntuKarmicXsplash](https://wiki.kubuntu.org/KubuntuKarmicXsplash)

It seems as though this might not happen anyway.

> Note this project is very delayed, it may not be available in karmic or may be implemented later as an update

---

### Post by ranch hand on 2009-10-15
Look in /usr/share/images and see if there is a folder for xsplash or what ever screwy thing KDE is using.  If the image is as good as in xsplash you are not missing much.  On the other hand it is easy to replace the image with one of your own.

---

### Post by MTGap on 2009-10-16
Yeah I guess it appears at the moment I just have to use xsplash and I have no issue with that, I just looked and yes there is a folder for xsplash now with the images inside, before my install of it there was no such folder. 


I'll have to change it, brown doesn't go well with KDE, at least with my current plasma theme.

---

### Post by inportb on 2009-10-16
Though... I don't see anything wrong with not using xsplash. The bootsplash has nothing to do with whatever screwy thing KDE might be using, but usplash works.

---

### Post by MTGap on 2009-10-16
Nice to see you inportb; I just read somewhere that xsplash had some advantages over usplash in terms of boot performance. 

By the way, now with Grub2 and no menu.lst Where am I supposed to modify my menu entries, currently I have no splash screen at all because splash isn't in the entry. Do I have to do this at bootup, to edit the line.

---

### Post by Longinus00 on 2009-10-16
> **MTGap said:**
> Nice to see you inportb; I just read somewhere that xsplash had some advantages over usplash in terms of boot performance. 

By the way, now with Grub2 and no menu.lst Where am I supposed to modify my menu entries, currently I have no splash screen at all because splash isn't in the entry. Do I have to do this at bootup, to edit the line.

That splash line in grub2 only controls usplash loading. If you want xsplash to work it's going to take a little more work than that. Have you tried asking in the kubuntu forum/mailinglist?

---

### Post by inportb on 2009-10-16
The boot performance improvement is with loading Xorg earlier in the pipeline. This enables use of xsplash, but it is by no means necessary to use xsplash. Unfortunately, I don't think it's possible to continue running usplash once Xorg has initialized, so the effect would be a frozen usplash.

The transition to early Xorg hasn't occurred yet. I believe Ubuntu-Gnome users see a substantial bit of usplash before xsplash takes over. Is this true?

---

### Post by MTGap on 2009-10-16
Do you by chance now then how to enable either xsplash or usplash?

---

### Post by inportb on 2009-10-16
I haven't had any experience with xsplash, and usplash shows up just fine for me without my having to do anything.

---

