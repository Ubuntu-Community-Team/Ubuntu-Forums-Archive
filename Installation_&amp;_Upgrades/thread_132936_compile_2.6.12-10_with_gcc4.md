---
title: "compile 2.6.12-10 with gcc4"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by PsychoTrauma on 2006-02-19
I have the source repos enabled and would like to build a default kernel image with gcc4 instead of gcc3.4. What would be the apt-src command to get all deps and build the 2.6.12-10 kernel?

---

### Post by tseliot on 2006-02-19
Why don't you use gcc-3.4???

I don't know if it's possible to compile it with gcc-4.0

---

### Post by PsychoTrauma on 2006-02-19
There is no special reason I would just prefer it use gcc4 so I don't need gcc3.4 installed. A search found "apt-get build-dep" and that looks interesting as well.

It seems using both of those gives the same results, the kernel wants to be compiled with gcc-3.4. Is there a config file I could edit to make it use gcc-4.0 instead?

Maybe I will use one of your guides tseliot to get a new vanilla kernel and just copy over the config file from ubuntu it will probably be easier.

---

### Post by tseliot on 2006-02-19
[QUOTE=PsychoTrauma]There is no special reason I would just prefer it use gcc4 so I don't need gcc3.4 installed. A search found "apt-get build-dep" and that looks interesting as well.

It seems using both of those gives the same results, the kernel wants to be compiled with gcc-3.4. Is there a config file I could edit to make it use gcc-4.0 instead?[/QUOTE]
I think it just won't compile with gcc-4.0 but, since I'm not a kernel hacker (or at least that experienced), I hope somebody can answer your question (if an answer exists).

Regards

---

### Post by Rizado on 2006-02-19
Just compile the newest kernel instead, it's much faster and works with gcc 4

---

### Post by PsychoTrauma on 2006-02-19
Tseliot i'm going to use your HOWTO: Kernel Compilation for Newbies guide and compile the newest stable kernel.org kernel instead since that will probably be easier. Your guide is very good but the kernal.org parts are a bit scattered around. If you don't mind I would like to post exactly what I needed to do/change in your guide for the newest kernel.org kernel. Maybe if you're not too busy you can take the info and maybe split your howto into two sections to make it a bit easier for people who want to do a kernal.org compile.

---

### Post by tseliot on 2006-02-19
[QUOTE=PsychoTrauma]Tseliot i'm going to use your HOWTO: Kernel Compilation for Newbies guide and compile the newest stable kernel.org kernel instead since that will probably be easier. Your guide is very good but the kernal.org parts are a bit scattered around.[/QUOTE]
I know that. I'll see what I can do to solve the problem
[QUOTE=PsychoTrauma]If you don't mind I would like to post exactly what I needed to do/change in your guide for the newest kernel.org kernel. Maybe if you're not too busy you can take the info and maybe split your howto into two sections to make it a bit easier for people who want to do a kernal.org compile.[/QUOTE]
I'm working on a translation at the moment. Nonetheless I would be glad to receive any feedback. You can post it in my guide so that I could use it as soon as I have some spare time.

---

