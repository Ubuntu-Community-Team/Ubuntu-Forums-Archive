---
title: "sources.list - 13: Permission denied)"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by johnata on 2010-01-25
[SIZE=3]Someone could help me?

Appear sometimes ago a message:
E: Opening /etc/apt/sources.list - ifstream::ifstream (13: Permission denied)

I'm trying update my computers but I don't get.. Please.. All my docs, movies and pictures are in this PC... What Can I Do to fix?[/SIZE]

---

### Post by ibuclaw on 2010-01-25
Curious,

Can you run:
```
ls -l /etc/apt/sources.list
```
And post the output.

Regards
Iain

---

### Post by johnata on 2010-01-25
[SIZE=2]Appeared:

-rw-r--r-- 1 root root 3254 2010-01-25 17:32 /etc/apt/sources.list

Please, answer me... u.u
[/SIZE]

---

### Post by ibuclaw on 2010-01-26
Hmm, seems fine, perhaps there are some other attributes at play here.

Oh well, perhaps creating a new file will resolve it.

```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo cat /etc/apt/sources.list.old | sudo tee /etc/apt/sources.list

```

Regards
Iain

---

