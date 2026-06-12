---
title: "LPIA netboot issues"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kingborel on 2009-08-02
Ok I'm having a small problem booting from the LPIA-based netboot .img. I can write it to my USB key and boot it, but it just resets the laptop after reloading the intrid.gz file. It works fine when I use the i386 img. Is this a sign that my MSI Wind U100 (atom processor) doesn't support the LPIA kernel? Or is it just a bad build of the img?

---

### Post by jbernardo on 2009-08-02
Try yesterday's (20090801) build. For me (Aspire One) only failed at tasksel, and I was able to go on from there. Check my post [here]("http://ubuntuforums.org/showthread.php?t=1229446"). 
After it boots you can install UNR or Gnome, I just chose kubuntu-netbook because I like kde.

---

### Post by kingborel on 2009-08-02
Thanks, I was trying the netboot install but I'll grab the full ISO from the link in your post (why is it in the ports tree, no wonder I couldn't find it). Hopefully it goes smoothly. I'll post back with results

---

