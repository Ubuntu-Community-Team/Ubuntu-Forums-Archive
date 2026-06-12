---
title: "Multitran compilation problem (programmer's help is needed)"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by ndmitry on 2012-04-06
Hello everyone!

I need some help. I got used to Multitran demo dictionary (which is free and has 1'000'000 words database).
Here's [*a link*]("http://www.multitran.ru") to their site multitran.ru  (there is an translation into English) and here is [*a link*]("http://multitran.sourceforge.net") to the open source code version from sourceforge.net
 
I was trying to compile it but got stuck on the 5th library **mt-utils**.

Here is an output ( *[link to the file]("http://ubuntuone.com/63ZsQNkxsXfzYhbkc6mMb5")* ) while trying to do this:
```
sudo make install
```

Compiler isn't able to resolve references (there is a lot of "undefined references") to the functions declared in 4th library, **libmtquery**[B].

[/B]So the question is how to rewrite make-files or source files to make it work?
P.S. I deleted testsuite directory from makefile (to compile only src directory):
```
SUBDIRS = src testsuite
```

Thanks for your help!

---

