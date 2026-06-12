---
title: "Update Error: vivid release no longer has a file"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by colmeweb on 2018-05-09
I am trying to update to 18.04 but i am getting a strange error message.

E:The repository 'http://archive.canonical.com/ubuntu vivid Release' no longer has a Release file.

Not sure how to get around this.

Any Takers?

---

### Post by oldos2er on 2018-05-09
You've a Vivid source in either /etc/apt/sources.list or /etc/apt/sources.list.d/. Support for it ended in Feb. 2016.

Can you post the results of ```
cat /etc/apt/sources.list
``` and ```
ll /etc/apt/sources.list.d
```?

---

