---
title: "Netbook Remix Update Greyed out?"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mxboy15u on 2009-09-27
I am running UNR 9.10 and the latest netbook remix update is greyed out and cannot be selected. Is there a way to re-enable it, why would it be greyed out but visible?

---

### Post by taavikko on 2009-09-27
What does it say if trying to upgrade via terminal
```
sudo aptitude update && sudo aptitude full-upgrade
```

Most likely dependencies issue (either needs something installed or it's going to remove something)

---

### Post by mxboy15u on 2009-09-27
That seems to have worked. Thanks.

---

