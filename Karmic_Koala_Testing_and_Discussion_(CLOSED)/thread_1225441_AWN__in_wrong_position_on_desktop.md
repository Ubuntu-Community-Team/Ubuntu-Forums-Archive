---
title: "AWN  in wrong position on desktop"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-28
I just install Avant Window Navigator but it displays itself at the top of the desktop. To be precise, the bar is at the top center, with the applets/icons at the top left.

I haven't tried it from ppa yet to see if there's a difference.

---

### Post by phenest on 2009-07-28
PPA does the same. Both also freeze up everything but the mouse cursor (something posted in another thread).

---

### Post by anders_c_ on 2009-07-28
It doesnt work at all for me...:(
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/398008](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/398008)

---

### Post by tjeremiah on 2009-07-28
so i take it that the AWN issue has been resolved? (100% cpu hogging?)

---

### Post by wayne_cat on 2009-07-28
> **tjeremiah said:**
> so i take it that the AWN issue has been resolved? (100% cpu hogging?)

No ... still 100% CPU usage (awn and xorg process)

---

### Post by phenest on 2009-08-10
> **wayne_cat said:**
> No ... still 100% CPU usage (awn and xorg process)

Is a fix due? Can't do any testing of AWN until.

---

### Post by wayne_cat on 2009-08-10
> **phenest said:**
> Is a fix due? Can't do any testing of AWN until.

Todays GTK+ update should have fixed the problems with AWN.

edit: I was wrong ... he bug has been fixed upstream ... but the version from this ppa:

[https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008/comments/45](https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008/comments/45)

works on my system

---

### Post by phenest on 2009-08-12
AWN is now working! Woo hoo! Goodbye gnome-panel. Although I did notice with the weather applet, the change location window stays behind the applet preferences window. A bug for AWN applets, me thinks.

EDIT: As a warning: Don't get rid of your gnome-panel yet!

---

### Post by tjeremiah on 2009-08-12
> **phenest said:**
> AWN is now working! Woo hoo! Goodbye gnome-panel. Although I did notice with the weather applet, the change location window stays behind the applet preferences window. A bug for AWN applets, me thinks.

EDIT: As a warning: Don't get rid of your gnome-panel yet!

*jumps for joy*

---

### Post by phenest on 2009-08-12
Why is this? Awn is at the top under the gnome panel, yet Firefox won't cover the area where AWN should be. And yet, I have Karmic in a VM which has AWN in the right position.:confused:

---

### Post by tjeremiah on 2009-08-12
for me, at least, it interfares with compiz. Meaning, if compiz is enabled, along with awn, compiz doesnt work.

---

### Post by wayne_cat on 2009-08-12
strange ... Compize is active and AWN works as expected here

---

### Post by phenest on 2009-08-13
I'm using Metacity. Can some one test theirs with Metacity instead please?

---

### Post by wayne_cat on 2009-08-13
> **phenest said:**
> I'm using Metacity. Can some one test theirs with Metacity instead please?

works

[[IMG]http://ubuntu-pics.de/thumb/21786/bildschirmfoto_Go29ZX.png[/IMG]]("http://ubuntu-pics.de/bild/21786/bildschirmfoto_Go29ZX.png")

edit: errors in .xsession-errors?

cat .xsession-errors |grep -i awn

---

### Post by phenest on 2009-08-13
Thanks wayne_cat. This is strange as my VM install is ok. I think I'm gonna  look at a few things, error logs, try with Compiz. Then maybe try a fresh install to see what happens.

---

### Post by wayne_cat on 2009-08-13
> **phenest said:**
> Thanks wayne_cat. This is strange as my VM install is ok. I think I'm gonna  look at a few things, error logs, try with Compiz. Then maybe try a fresh install to see what happens.
  

another idea ... create a new user and test it... maybe your AWN configuration is "damaged"

---

### Post by phenest on 2009-08-13
I think I had a borked installation. I reinstalled alpha 3, updated, and it works fine. Don't know what happened though. I had hardly changed Karmic from default. Oh well, doesn't matter, as all is well now. Thanks to all for any suggestions.

---

