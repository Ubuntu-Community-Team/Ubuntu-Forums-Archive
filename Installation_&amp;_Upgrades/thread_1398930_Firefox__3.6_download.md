---
title: "Firefox  3.6 download"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by emms_gb on 2010-02-05
Hello!
i have just downloaded firefox 3.6.ta.bz2 onto my desktop and would now like to install. Currently using firefox 2. Could some one give me list of commands so I can update my browser? Very grateful

Emma

---

### Post by kaspien on 2010-02-05
> **emms_gb said:**
> Hello!
i have just downloaded firefox 3.6.ta.bz2 onto my desktop and would now like to install. Currently using firefox 2. Could some one give me list of commands so I can update my browser? Very grateful

Emma

Running apt-get update would bring you up to Firefox 3.5.7
If you want to run 3.6, note that many of the plugins won't support it because they haven't been updated by their authors.

If you still want to do it:

$ sudo apt-get build-dep firefox
$ tar xvjf firefox.tar.bz2 
$ cd firefox (whatever the directory name is)
$ make -f client.mk build

You may need to apt-get install build-essential

After it's done you can run: ~/firefox/firefox/dist/bin/firefox

You may need to adjust the paths.

---

