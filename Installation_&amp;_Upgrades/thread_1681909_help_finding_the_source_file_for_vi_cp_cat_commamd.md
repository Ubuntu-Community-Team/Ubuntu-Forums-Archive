---
title: "help finding the source file for vi cp cat commamds"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by priyamvaidya on 2011-02-05
hi

i am somewhat new to ubuntu 10.10 (Maverick meerkat)  


[LIST=1]
[*]i want to find the source file (.c) file for cat, vi, cd commands.  Where are these files located.  i searched /usr/src but  unable to locate these files.
[*]how to edit/update anyone of this file .
[*]once edited, how to compile and make the program work
[/LIST]

help is appreciated

---

### Post by oldos2er on 2011-02-05
vi source is here: [http://ex-vi.sourceforge.net/](http://ex-vi.sourceforge.net/)

cat is part of the coreutils package, to download the source code for it run ```
apt-get source coreutils
```

cd is a shell command, more info here: [http://ss64.com/links/bash.html](http://ss64.com/links/bash.html)

---

