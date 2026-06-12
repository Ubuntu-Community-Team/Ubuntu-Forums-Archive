---
title: "When using apt-get, how to find path that the package has been installed?"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by jutirain on 2007-07-09
I installed a programming library, opencv for computer vision programming in cpp, using the following command:

sudo apt-get install libcv-dev libcvaux-dev libhighgui-dev

However, according to the [official wiki of opencv]("http://opencvlibrary.sourceforge.net/CompileOpenCVUsingLinux"), I should know about the exact path where the source code has been placed, to direct g++ to the right linking path.

But, actually, I totally have no idea where the source code of opencv is. I don't where apt-get stored it.

I tried to use locate opencv, locate libcv, some thing like that, however, it returns nothing...

So, how to find path that the package has been installed?

p.s I'm using ubuntu 7.04

---

### Post by moore.bryan on 2007-07-09
[I]chances are, they're in /lib, /usr/lib, or /usr/local/lib.  oh, and a nice low-resource search tool you might find more useful is [catfish]("http://software.twotoasts.de/?page=catfish") (it's in the repos).
[/I]

---

### Post by luvr on 2007-07-09
You can type the following command to obtain a list of the files (including their full paths)  installed by a package:
```
dpkg-query --listfiles *packagename*
```
If you're a **"Synaptic Package Manager"** user, you can also view the list of files via the *"Properties"* window of the package: Right-click the package in the list, select *"Properties,"* and select the *"Installed Files"* tab.

---

