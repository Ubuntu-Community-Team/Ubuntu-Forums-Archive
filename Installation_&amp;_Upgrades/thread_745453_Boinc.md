---
title: "Boinc"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by CBribiescas on 2008-04-04
I've installed BOINC and its running properly, but it seems to have dumped a bunch of config files right into my home directory, does anyone know how to change the directory of where these files are located so that they don't have to be in my home directory?

---

### Post by dabang on 2008-04-04
I guess BOINC dumps the files in your working directory, so you'll have to start it from within your BOINC directory or create one. You could make a small script for this

```
mkdir ~/.boinc_dir
```
script:
```
#!/bin/bash
cd ~/.boinc_dir
/path/to/boinc_bin
```

---

