---
title: "System Beep tab"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by guillepb on 2008-10-15
Is the "system beep" tab on System > Preferences > Tab gone for good?

I miss it! I hate the system beep and the alternatives to mute it are all too cumbersome :(

---

### Post by inportb on 2008-10-15
Is *blacklist pcskpr* too cumbersome for you?

---

### Post by PinkFloyd102489 on 2008-10-15
```
sudo rmmod pcskpr
```

That'll get rid of it. To get it back do:

```
sudo modprobe pcspkr
```

---

### Post by FuturePilot on 2008-10-15
In the sounds preferences try unchecking the "Play Alert Sound" box. It should play a sound but instead it seems to act as the system beep.

---

