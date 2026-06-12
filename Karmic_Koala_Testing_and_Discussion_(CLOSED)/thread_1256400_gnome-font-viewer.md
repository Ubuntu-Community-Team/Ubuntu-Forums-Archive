---
title: "gnome-font-viewer"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-09-02
gnome-font-viewer don't work here. it's not possible to start it.
anyone experienced the same?

---

### Post by taavikko on 2009-09-02
Working correctly here.

Test with:
```
gnome-font-viewer /usr/share/fonts/truetype/ttf-arabeyes/ae_Metal.ttf
```

If running so much problems, add a new user and test the functions with it.
I fthey work, something has messed up your $HOME

---

### Post by pulpo69 on 2009-09-02
i tried it with a new user, but with the same result.  ??

---

### Post by taavikko on 2009-09-02
> **pulpo69 said:**
> i tried it with a new user, but with the same result.  ??

Is system up-to-date (main server)
```
sudo aptitude update && sudo aptitude full-upgrade
```

Does it print out an error?

---

### Post by pulpo69 on 2009-09-02
no error output.

---

