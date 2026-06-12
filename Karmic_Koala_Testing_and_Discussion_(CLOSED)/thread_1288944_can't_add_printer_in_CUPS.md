---
title: "can't add printer in CUPS"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by renkinjutsu on 2009-10-12
localhost:631
click administration
click add printer

type in user and password

it says Forbidden! .. anyone else have this problem? know a fix?

---

### Post by Martje_001 on 2009-10-12
```
sudo adduser <user> lpadmin
```

---

### Post by renkinjutsu on 2009-10-12
thanks for the reply, but i meant to mark it solved earlier when i had a look at my cupsd.conf and saw the group name

i got distracted because chromium crashes on that page and i spent the better part of my time trying to reinstall firefox on my flakey internet connection

---

