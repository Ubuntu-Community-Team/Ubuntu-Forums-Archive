---
title: "Directory location problem"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by osowo on 2008-10-14
good day ,I tried installing vuze_linux.tar.bz2 using command terminal,I could not get to my desktop directory through the CLI terminal.
when i type "cd /desktop" . i get the following report:
_bash:cd: /home/osowo/desktop:no such file or directory_
i need your help,please
p.s same problem with documents and music directories.

---

### Post by kosmiciatakuja on 2008-10-14
Try
```
cd ~/desktop 
```
or 
```
cd ~/Desktop
```

This is case sensitive, remember, so Desktop is a different directory than desktop!

---

