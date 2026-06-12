---
title: "Update to python3 and make primary compiler"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by cheerPuncH on 2013-01-15
Hi,

I've googled this and thought it would be easy, but it seems it's not very straight forward.

I'm working on an Ubuntu 10.04.2 server with python version 2.6.5.

I need to update to Python3. I downloaded and installed Python3.3 in /, but I don't know where I should put it and furthermore, when I do the $python -V command, it still returns 2.6.5. Where do I put Python3.3 and how do I make it my primary compiler? (I know not to delete Python 2.6.5 because of system dependencies)

Thanks,
Jeri

---

### Post by Cheesemill on 2013-01-15
No need to download anything manually, Python 3 is in the repos.
```
sudo apt-get install python3
```

---

### Post by cheerPuncH on 2013-01-15
perfect

---

