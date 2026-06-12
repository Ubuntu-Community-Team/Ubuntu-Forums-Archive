---
title: "How to start eclipse???"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by sjosh_theone on 2007-11-23
hey guys I just installed the following 3 packages from Universe rep.:--
eclipse-jdt
eclipse-platform
eclipse-rcp
But the embarrassing question is how to start eclipse?I cant even find  the appropriate file. 
Forgive me for asking such a lame question. 
Thanks in advance.

---

### Post by ioniviil on 2007-11-23
the best I can recommend you is to download eclipse straight from the site (there is the very las version), You'll get a tar.gz file (if my memory is not failing), just unzip it and start using it. The file you will need to execute is the one named "eclipse", it is an executable file so you should have no problems. Note that if just by chance you've got installed the gcj and  (gnu compiler for java) gij (gnu bytecode interpreter for java) the eclipse will probably crawl instead of run, because those interpreters do not understand java1.6, so you'll need to uninstall them, then download the jre from Sun's site, install it, and just then, will the eclipse work as it is supposed.

I am totally new to Ubuntu and Linux, so don't expect absolute correctness from me, I hope this works for you as it did for me. Good luck!

(A recommendation: Use Netbeans from Sun, it's way much better).

---

### Post by GavinZac on 2007-11-23
i just installed the eclipse package and synaptic took care of the rest

---

### Post by jken146 on 2007-11-23
Did you install the package eclipse?

---

### Post by maxaldana on 2007-11-26
Hi!

Just  install the eclipse package, which is already in the Ubuntu repositories. Go to

System -> Administration -> Synaptic package manager

look for eclipse ans install it. 

After the installation, the eclipse icon should appear in the Applications -> Programming menu. Another option is to open a terminal (Applications -> Accessories -> Terminal) and type "eclipse" (without the quotes). 

The third possibility is to download the eclipse package directly from the eclipse-project web page ([www.eclipse.org](www.eclipse.org)). The package is already functional. You just have to uncompress the package:

gunzip eclipse.XXX.tar.gz
tar -xvvf eclipse.XXX.tar

This will create a directory named "eclipse", in which there is a "bin" subdirectory. Inside the bin subdirectory there is the program eclipse, fully functional. You just have to open a terminal, move to the bin subdirectory of the eclipse directory, and type ./eclipse

I would recommend the first option, namely, to install eclipse via the  Synaptic package manager.

Best.

---

### Post by owlstead on 2008-05-03
One important thing about the Eclipse packages: it seems you will have to install the "eclipse" package, otherwise you won't have an icon or shell script to startup eclipse. Strangely enough this package will not become automatically selected if you install e.g. the eclipse java development package.

I just found this out by trying (brand new 8.04 hh installation, unstable as hell - probably caused by Audigy or other sound card).

---

