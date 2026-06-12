---
title: "[SOLVED] Intrepid Ibex (please help)"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2008-09-26
I run Intrepid Ibex 64 bit and for some reason yesterday, my Home folders appeared on my desktop (they're in my home/username folder also). I deleted the ones off my desktop, and the ones in my home folder dissapeared. I restored them to my folder and they reappeared. I went back to Hardy Heron, same problem. Any help on this would be appreciated greatly.

---

### Post by Sef on 2008-09-26
Moved to Intrepid Ibex forum.

---

### Post by Sand &amp; Mercury on 2008-09-26
Sounds like your desktop is set up to show your home folder contents on it...

---

### Post by forumache on 2008-09-27
> **Sand & Mercury said:**
> Sounds like your desktop is set up to show your home folder contents on it...

Where can this be set correctly?

I remember having this problem about 6 months ago and fixed by changing one key in gconf-editor, but I cannot seem to find it again.

---

### Post by mc4100 on 2008-09-27
Could be wrong, but I think Ubuntu Tweak can also change this. Do you have it installed?

---

### Post by marmuta on 2008-09-27
The key in gconf-editor is
/apps/nautilus/preferences/desktop_is_home_dir

You can find it next time if you use the search function in gconf-editor with "home".

---

### Post by forumache on 2008-09-27
Please see this bug, it shows you where you should look:

[https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs-gtk/+bug/262553](https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs-gtk/+bug/262553)

Thanks marmuta, I was searching for Desktop ;)

---

