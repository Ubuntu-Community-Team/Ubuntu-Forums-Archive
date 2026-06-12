---
title: "changing default keyboard on 11.04 server"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by dormant on 2011-05-24
I installed Ubuntu 11.04 server and left the keyboard as default (US).

I now want to change the default keyboard to be GB.

How can I change the default keyboard from the command line?

---

### Post by sisco311 on 2011-05-24
```
sudo dpkg-reconfigure console-data
```

---

### Post by dormant on 2011-06-02
Thank you.

console-data was not installed by default when I installed Ubuntu server (LAMP). So I set the keyboard when I installed it.

---

