---
title: "error dpkg code 1"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by jorissansen on 2014-02-15
Hello, 
I think I ave an error with my computer, i'm totally unable to install or uninstall a package, i get thoses error:

 python-setuptools
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't know what to do, and i can't find anything on the web that can help me...

---

### Post by Jonathan Precise on 2014-02-15
Try:

```
sudo apt-get -fy install > $HOME/Desktop/results.txt 2>&1
```

Attach the results.txt file.

---

