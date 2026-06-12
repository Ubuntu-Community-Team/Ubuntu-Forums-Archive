---
title: "NO terminal"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mick222 on 2009-10-10
I reinstalled Karmic after i broke my system the other day. It seemed to go well i have Karmic installed and a separate home partition. I updated via terminal as I thought it would be safer.

> sudo aptitude update && sudo aptitude upgrade

Now terminal gives me an error > There was an error creating the child process for this terminal I have no software center synaptic and update manager don't work either and a seperate issue sound device is not found.

---

### Post by jeremyswalker on 2009-10-10
Not necessarily an answer to your problem, but shouldn't:
```
sudo aptitude update && sudo aptitude upgrade
```
be
```
sudo aptitude update && sudo aptitude **safe-**upgrade 
```

---

### Post by mick222 on 2009-10-10
probably should have been I'm a bit stupid when it comes to terminal lol. 
Is there no way to get terminal back.

---

### Post by jeremyswalker on 2009-10-10
I'm not real sure what to do here. However, you should be able to get to a console by pressing > "Ctrl + Alt + F1". Then you could do what you need to do on the command line to try and fix the situation. You can get back to X by pressing > "Ctrl + Alt + F7".

---

### Post by FuturePilot on 2009-10-10
Make sure /dev/shm and /dev/pts are mounted. That error usually means that those two things are not mounted.

---

### Post by mick222 on 2009-10-10
thx Fixed ran upgrade from console ctrl->alt->f1 seemed to fix it . But i did get a segmentation fault trying to install a file Flickernet.dll , is dll not a windows file type?

---

### Post by jeremyswalker on 2009-10-10
I did a quick search, and it looks like flickernet.dll does actually belong to some program on Linux. Probably used with one of the mono apps.

---

### Post by mick222 on 2009-10-10
yes think it belongs to mono updates on restart anyway thx

---

