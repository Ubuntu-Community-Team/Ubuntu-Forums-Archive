---
title: "luit doesn't work properly!"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by anaconda on 2010-03-15
luit works, BUT when I finish the connection/program I were running with luit, gnome-terminal just hangs! (same happens with konsole)

(in 9.10 exiting from programs run through luit worked)

Is there any way to resume the terminal.. I tried among other things Ctrl-c, Ctrl-z, exit, quit, etc, with no results.

Does luit work with anyone else?

it doesn't matter what I run with luit. the terminal will hang.
eg:
```
luit -encoding ISO-8859-15 ping -c 4 www.google.com
```
will ping [www.google.com](www.google.com) 4 times, and then exit, but the terminal hangs..

the same happens when running 
luit -encoding ISO-8859-15 telnet xxxx
luit ssh xxxx
luit -encoding ISO-8859-15 irssi
When you exit the program terminal hangs..

---

### Post by anaconda on 2010-03-15
ok. this is reported in launchpad. Didn' notice that ending a luit session hangs gnome-terminal AND eats 100% of processor (or 1 processor if many)

---

