---
title: "Update Python ?"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by Ric95 on 2006-12-22
I found the version of Blender I want to install ( its here: [http://ruicampos.com/fl_tmp/debian/ubuntu-dapper/]("http://ruicampos.com/fl_tmp/debian/ubuntu-dapper/") but thats not my question)
It installs ok, but when I try to run it I only get this error.;
> blender-bin: error while loading shared libraries: libpython2.4.so.1.0: cannot open shared object file: No such file or directory 
The repositories seem to give me python 2.3. 
How can I upgrade that? Would 'sudo apt-get update python 2.4' work ?

---

### Post by meng on 2006-12-22
What version of Ubuntu are you using? I think 6.06 and 6.10 come with 2.4, but maybe not 5.10.

---

### Post by Ric95 on 2006-12-22
Dapper 6.04 ( beta,- synaptic upgraded. ( it thinks its up to date....)

---

### Post by meng on 2006-12-22
Python 2.4 comes with Dapper (just confirmed it on a package search). I can't explain why you don't seem to have it. Have you confirmed that you have 2.3 installed (just type python at the command line, the shell will tell you what version you have, ctrl-d to exit I think).

---

### Post by Ric95 on 2006-12-22
You're right, the terminal says I have 2.4.2. 
I was looking at synaptic, it shows 2.4.2, yet it also shows 2.2.3 installed.  Odd.
Does that error message help?

---

### Post by meng on 2006-12-22
The error message just says it can't find the library in the place it is looking for it. So it may be looking in the wrong place (or for the wrong name). Perhaps you need to look further for another deb of the blender version you are interested in.

---

