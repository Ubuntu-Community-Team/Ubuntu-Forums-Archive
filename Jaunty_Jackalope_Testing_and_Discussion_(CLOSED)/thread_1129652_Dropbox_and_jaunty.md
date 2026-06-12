---
title: "Dropbox and jaunty"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-04-18
Has anyone gotten dropbox to work on jaunty? It refuses to work for me

I downloaded the newest package just now

installed the deb

it told me to log out and log back in, which i did

then it said 'ok i need to install the daemon now', downloaded it, and then after it finished, it completely locked up gnome, and i had to ctrl+alt+f1 and type 'killall dropbox' to get my computer to be usable again

and now if i launch dropbox, it just segfaults right away.

so.......how exactly do i do this? It works if i run it as root....but then i cannot edit or save stuff to my dropbox folder....

---

### Post by Bou on 2009-04-18
What's the benefit of dropbox over, say, conduit + box.net?

---

### Post by Polygon on 2009-04-18
conduit never worked well for me. And....conduit is a linux only program, i also use windows =)

either way, you are dealing with proprietary stuff....box.net doesn't exactly have ITS source open either =P

but if someone made a dropbox style program where you could specify your own hosting or webspace, that would be awesome.

---

### Post by dentaku65 on 2009-04-19
Dropbox works like a charm here.
Try to rename your dropbox folder
```
mv ~/Dropbox ~/Dropbox.bak
```
reboot and reaload the app./daemon

---

### Post by Gilabuugs on 2009-04-19
works fine here too on both 64 bit and 32 bit, I downloaded the 8.10 releases and just used those, worked right out of the 'box'

---

### Post by Polygon on 2009-04-19
for some reason its working now, but its buggy as sin and keeps crashing, usually related to when i click the tray icon

it also segfaults when you move the dropbox folder, which i accidentally did when i was trying to add it to my favorites list in nautilus...hehe

---

### Post by Gilabuugs on 2009-04-19
That is weird, just tried both of those (tray icon and moving it) a few different ways and no problems maybe remove and reinstall dropbox

---

### Post by Polygon on 2009-04-19
yeah i'm not sure whats going on, now its working but its not syncing my files (its just sitting there stuck on downloading 32 files)....

posted a support thread here: [http://forums.getdropbox.com/topic.php?id=8525&replies=1#post-54229](http://forums.getdropbox.com/topic.php?id=8525&replies=1#post-54229)

---

### Post by dentaku65 on 2009-04-19
> **Polygon said:**
> yeah i'm not sure whats going on, now its working but its not syncing my files (its just sitting there stuck on downloading 32 files)....

posted a support thread here: [http://forums.getdropbox.com/topic.php?id=8525&replies=1#post-54229](http://forums.getdropbox.com/topic.php?id=8525&replies=1#post-54229)

Did you reboot your box after the install?

---

