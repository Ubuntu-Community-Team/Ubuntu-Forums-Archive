---
title: "Disable gdm at start-up (Karmic Koala 9.10)"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PANNY on 2009-10-05
Is it possible to disable gdm at start-up in Karmic (login in a shell after boot)? I know there are some changes from previous versions of Ubuntu.

---

### Post by cariboo on 2009-10-05
Use update-rc.d to stop gdm from starting. This will work for any version:

```
sudo update-rc.d -f gdm remove
```

then when you want to start X at the prompt type:

```
startx
```

---

### Post by hryamzik on 2009-10-28
Doesn't work for me on 9.10. It simply loads again on startup... Updating now and will disable autologin after update.

I've also ran apt-get purge usplash, didn't help either.

---

