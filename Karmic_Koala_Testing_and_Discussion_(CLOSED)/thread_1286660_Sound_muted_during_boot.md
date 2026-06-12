---
title: "Sound muted during boot"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by akernan on 2009-10-09
I have a problem of the sound being muted after booting.  I can unmute the sound after the boot.  It's annoying to have to do this every time.  My sound worked fine in Jaunty, I've been dealing with this problem for a couple months since I upgraded to Karmic.  I always hoped new kernel releases would fix my problem.  What can I do to fix this?

---

### Post by andrewabc on 2009-10-09
> **akernan said:**
> I have a problem of the sound being muted after booting.  I can unmute the sound after the boot.  It's annoying to have to do this every time.  My sound worked fine in Jaunty, I've been dealing with this problem for a couple months since I upgraded to Karmic.  I always hoped new kernel releases would fix my problem.  What can I do to fix this?

I'm pretty sure this was a bug early on in karmic, but I think they fixed it. Maybe it is not fixed for you since you upgraded. Maybe try the beta and see if it has similar problems.

---

### Post by akernan on 2009-10-09
I don't want to reinstall. Can I fix this some other way?

---

### Post by kansasnoob on 2009-10-09
> **akernan said:**
> I don't want to reinstall. Can I fix this some other way?

I managed to work it out by installing 'gnome-alsamixer' and tweaking the toggles there, then "un-muting" the volume applet and subsequent reboots have remained stable .............. well, most of the time!

To install either go to synaptic or run:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video.

---

### Post by akernan on 2009-10-09
I installed gnome-alsamixer and played with it.  It didn't seem too fix my problem.  My soundcard preferences are not saved.  Any other ideas?

---

### Post by akernan on 2009-10-12
Bump

---

