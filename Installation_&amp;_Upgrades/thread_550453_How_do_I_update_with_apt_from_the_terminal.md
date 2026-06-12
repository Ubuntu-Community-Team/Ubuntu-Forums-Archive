---
title: "How do I update with apt from the terminal?"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by G_Stewart on 2007-09-13
I've been having trouble with a file called sherpath, I can't use any graphical system to update. Thought I'd try the terminal.

Gary

---

### Post by ubuntu27 on 2007-09-13
This updates the repositories:

```
sudo aptitude update
```

And this updates the application software:

```
sudo aptitude upgrade
```

---

