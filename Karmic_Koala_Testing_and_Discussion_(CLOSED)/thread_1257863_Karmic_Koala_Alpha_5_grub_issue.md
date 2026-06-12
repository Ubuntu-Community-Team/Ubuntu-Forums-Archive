---
title: "Karmic Koala Alpha 5 grub issue"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by noob707 on 2009-09-04
I just did a fresh install of Karmic Koala Alpha 5. After the install was done it said to restart so i did but Grub doesn't recognize my Vista install on another partition. The alpha 4 did recognize my vista but alpha 5 doesn't. How can i add my vista OS to grub since the installation didn't find any other OS.

---

### Post by overdrank on 2009-09-04
Moved to Karmic Koala Testing and Discussion

---

### Post by kansasnoob on 2009-09-04
Just go to terminal and run:

```
sudo update-grub
```

Nine times out of ten that'll pick it up.

---

