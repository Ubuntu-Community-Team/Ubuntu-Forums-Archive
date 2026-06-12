---
title: "&quot;make&quot; problem"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by ubuntu_jazzbach on 2007-01-17
Hi !!!

I'm installing the wireless driver of my LapTop (Intel Pro ipw2200) but, I'm having problems when running the "make" command. I've searched over and over for this specific problem but haven't found any solution. The problem goes as as follows:

When using the command "make", the following error appears:

/bin/sh: Syntax error: "(" unexpected
make: *** [check_old] Error 2

How can I solve this problem ??? I beg you help me, please, pleaseee !!!!![-o< [-o<

---

### Post by public_void on 2007-01-18
After some searching it seems this bug has come up before ([http://www.bughost.org/bugzilla/show_bug.cgi?id=1163]("http://www.bughost.org/bugzilla/show_bug.cgi?id=1163")). One of the suggestions is to open up the file Makefile in your favourite text editor and on the first line write:
```
SHELL=/bin/bash
```

---

### Post by ubuntu_jazzbach on 2007-01-18
OK, as soon as I arrive to my home, I'll do it and report the result. Thanks !!! :D

---

### Post by ubuntu_jazzbach on 2007-01-18
Nope, it didn't work. I followed both your suggestion and the the instructions in [http://www.bughost.org/bugzilla/show_bug.cgi?id=1163](http://www.bughost.org/bugzilla/show_bug.cgi?id=1163) but neither worked :cry:

---

