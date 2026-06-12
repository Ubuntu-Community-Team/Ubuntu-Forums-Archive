---
title: "Source Code Installation"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by cypher95 on 2011-08-11
Can anybody tell me how to install source code that i've downloaded from sourceforge or something like that?

---

### Post by cgroza on 2011-08-11
If it is a tar.gz or something like that, you must extract it.
Now depending on the language there could be a Makefile or a setup.py.

You mush open your terminal and cd to the directory.

If there is a Makefile, you should be able to run make and that should compile it for you.
If it is a setup.py, 
```
run sudo python setup.py install
```
For more detailed information, there are tutorials online on how to install from source code.

---

### Post by MG&amp;TL on 2011-08-11
Usually in the top level directory , there's a README file. What source code is it?

---

### Post by cypher95 on 2011-08-11
its a tar.gz

---

### Post by MG&amp;TL on 2011-08-11
No, I meant what program? Tar.gz's can be extracted in archive manager (right click, open with...') to a convenient place, then I suggest you find the readme (if any). :)

Source codes are a prickly business, usually best to see if you can software centre or synaptic them first.

---

### Post by oldos2er on 2011-08-12
Source code needs to be compiled before it can be installed.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

And yes it would help to know the name of the program. Have you checked the repositories for it?

---

