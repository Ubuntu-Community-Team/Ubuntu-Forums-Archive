---
title: "Edgy upgrade somewhat botched."
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by zeroooooooooooo on 2007-04-12
I upgraded to edgy from dapper by editing the sources, which I now see is referenced to as "hacky" and buggy in the sticky thread at the top of the topic page.  Now I know why.  Every time I go into the update manager after if tells me I have updates to install, it says there are packages that I can't install and that I should run a distribution upgrade.  I then try to run a distribution upgrade (essentially from edgy to edgy) and it fails, saying I should report it as a bug.

What should I do?

---

### Post by taurus on 2007-04-12
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by zeroooooooooooo on 2007-04-12
That appears to have fixed the problem. Thanks.

---

