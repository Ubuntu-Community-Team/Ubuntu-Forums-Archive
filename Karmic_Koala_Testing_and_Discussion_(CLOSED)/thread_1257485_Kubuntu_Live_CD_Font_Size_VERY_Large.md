---
title: "Kubuntu Live CD Font Size VERY Large"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mltriebe on 2009-09-03
I have had this bug in the past and for the life of me I can not recall the fix.  I have tried a normal boot and safe graphics mode but no luck.  The fonts are so large I can not read anything on the screen.  if anyone can remember the fix that will be great.

Thanks, Mike

---

### Post by jbernardo on 2009-09-04
That is usually because X detected the wrong DPI for your screen. You can either add the 'Option "DPI"' entry to xorg.log and restart kdm (from a alt+f2 console) or add the entry '-dpi 96' to the ServerArgsLocal entry in /etc/kde4/kdm/kdmrc and (once again) restart kdm.

---

### Post by mltriebe on 2009-09-04
I can't read the screen to do that though.

Mike

---

### Post by jbernardo on 2009-09-04
> **mltriebe said:**
> I can't read the screen to do that though.

Mike


Not even when you switch to a text console (ctrl+alt+f2)?

---

### Post by mltriebe on 2009-09-05
No, that takes me to a login screen and I do not know the info to put there.

Mike

---

### Post by jbernardo on 2009-09-06
Ok, so at least that points to the problem being only with X doing a bad job detecting your monitor. At the login screen the user should probably be ubuntu or guest, without password. From there you can try my suggestions from the first post - edit krmconfig and restart kdm, or edit xorg.conf and restart kdm. I have a Fujitsu Amilo P1505 laptop, for which I need to keep a working xorg.conf file ready to copy to /etc/X11 on a live CD to avoid exactly the problem you're having with the fonts.

---

### Post by mltriebe on 2009-09-08
Thanks, that did the trick.  And my broadband wireless card works again!!!  It stopped working in 9.04.

Mike

---

