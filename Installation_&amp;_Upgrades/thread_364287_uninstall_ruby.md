---
title: "uninstall ruby"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by rob_909 on 2007-02-18
How do you uninstall ruby 1.8.5

There is no make uninstall for the program, and I know it isn't safe to just login as root and delete the entire file.........any ideas?

---

### Post by taurus on 2007-02-18
How did you install it?  Try something like

```
sudo aptitude remove ruby
```

---

### Post by rob_909 on 2007-02-19
i was able to remove it, but I had to go into amarok and specify for it to not go through ruby to find some of it's source packages. Thanks.

---

