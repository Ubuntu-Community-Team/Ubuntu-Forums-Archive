---
title: "Strange tabbing behaviour in /media"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whitethorn on 2009-10-14
Hi,

I noticed this a couple days ago.  When I mount a partition and I want to put it to a folder in media.  Whenever I type /me  and then tab to complete it, it automatically fills out /media/cdrom I have to manually backspace to media and write out the name of the folder. If I tab again it doesn't like the folders in media it goes right to cdrom again.

Oh and I noticed that in Preferences -> Keyboard Shortcuts  the Start a terminal option is gone :(  Is there some way to get it back?

---

### Post by mgol on 2009-10-14
Does it 'tab' properly when You write /media/x[Tab], where x is a beginning letter of one of Your media devices different than c?

And if You could post the output of:
```
ls -lA /media
```

---

### Post by whitethorn on 2009-10-15
> **mgol said:**
> Does it 'tab' properly when You write /media/x[Tab], where x is a beginning letter of one of Your media devices different than c?

And if You could post the output of:
```
ls -lA /media
```

Oh it working now, looks like a couple updates fixed the problem :)

---

