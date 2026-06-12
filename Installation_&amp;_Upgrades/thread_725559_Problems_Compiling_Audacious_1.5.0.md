---
title: "Problems Compiling Audacious 1.5.0"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by peterzigo on 2008-03-15
Hello,

I tried to compile the latest Audacious (1.5.0) on my Ubuntu Gutsy, but i always get a error message.
I compiled all dependencies and after i run "./configure" everything seems fine, but when i type "make", it shows me the following error Message, after compiling some parts of audacious.
So heres the error message:
```
Successfully compiled sync-menu.c.
main.o: In function `main':
/home/pano/audacious-1.5.0/src/audacious/main.c:1377: undefined reference to `g_thread_init'
collect2: ld gab 1 als Ende-Status zurück
Failed to link audacious!
make[5]: *** [audacious] Fehler 1
make[4]: *** [all] Fehler 1
make[3]: *** [subdirs] Fehler 1
make[2]: *** [all] Fehler 1
make[1]: *** [subdirs] Fehler 1
make: *** [all] Fehler 1

```
Fehler means error in german.

Does anyone know, where the problem is?

thanks in advance

---

### Post by Thanoulis on 2008-03-15
Why don't you try to just install it from the Synaptic? It's in the repos.

---

### Post by peterzigo on 2008-03-15
I had it installed, but it didn't show me greek letters (&#954;&#945;&#953; &#949;&#947;&#974; &#941;&#955;&#955;&#951;&#957;&#945;&#962; &#949;&#943;&#956;&#945;&#953;^^)
 SO i hoped that this would fix this

---

### Post by peterzigo on 2008-03-16
I tried to compile it  on my LinuxMint VM and there it gets succesfully compiled!

This is very strange!
Could i use the deb packages i created on my LinuxMint VM or will there be serious problems, beacause it was compiled on a Virtual MAchine?

---

### Post by disturbedite on 2008-03-27
> **Thanoulis said:**
> Why don't you try to just install it from the Synaptic? It's in the repos.
cuz the latest version in the repo (for hardy) 1.4.6.

UPDATE:
lastest version in hardy is now 1.5.  i'm using it now.

---

### Post by sylecn on 2008-04-05
I've compiled it on gutsy just today with no errors.

Since no error when you run "./configure", I guess the dependences are OK.
Have you run "make" before your last ./configure , if so, did you run "make clean" before "make" ?
That will sometimes disturb you and cause errors.

---

