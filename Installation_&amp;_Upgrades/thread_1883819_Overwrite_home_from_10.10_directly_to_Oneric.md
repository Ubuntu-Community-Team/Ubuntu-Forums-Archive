---
title: "Overwrite /home from 10.10 directly to Oneric?"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2011-11-20
I was using Ubuntu 10.10 and did quite a bit personalized setting and preferences adjustment. Now I've upgraded to Ubuntu 11.10 (skipped 11.04). Before doing that, I did a backup of my /home directory under Ubuntu 10.10.  My question is, can I safely overwrite Ubuntu 11.10's /home with the old one, expecting all my personal settings and preferences to remain the same? I just don't understand how smart a computer can be that even when it changed it still "understands" how I configured my system. Some expert please help give me an answer, thanks.

---

### Post by JRV on 2011-11-20
This is a guess: No

The switch to Unity was a big change.  There will be problems.  Many effects in compiz will conflict with Unity.

---

### Post by fantab on 2011-11-20
> **zhaotianwu said:**
> I was using Ubuntu 10.10 and did quite a bit personalized setting and preferences adjustment. Now I've upgraded to Ubuntu 11.10 (skipped 11.04). Before doing that, I did a backup of my /home directory under Ubuntu 10.10.  My question is, can I safely overwrite Ubuntu 11.10's /home with the old one, expecting all my personal settings and preferences to remain the same? I just don't understand how smart a computer can be that even when it changed it still "understands" how I configured my system. Some expert please help give me an answer, thanks.

**NO you CANNOT safely overwrite 11.10 /home with that of an older version**. Like the post above says, there will be many complications. The change from gtk2 to gtk3 is huge... your previous application configurations and preferences will clash with the new engine of Gnome 3. 

However, if you want those other folders like, Downloads, Pictures, Videos, etc, you can replace them in the New /home individually after making sure there are no hidden files in those folders.

---

### Post by Lars Noodén on 2011-11-20
I have overwritten /home, it works for me.  The missing configuration files get created when they are needed.  

But you can't do the overwriting while logged in to the GUI.  It is best to do it from a console.  e.g. ctrl-alt-f1  ctrl-alt-f7 will bring you back to the GUI.

---

