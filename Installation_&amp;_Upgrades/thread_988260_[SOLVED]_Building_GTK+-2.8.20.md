---
title: "[SOLVED] Building GTK+-2.8.20"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by maustin2 on 2008-11-20
Following the instructions found in the Install file, I am having the following problem

  ./configure works as expected
   make gtk+-2.8 returns the following
make: *** No rule to make target `gtk+-2.8'.  Stop

What am I doing wrong???

---

### Post by Partyboi2 on 2008-11-20
Have you got build-essential package installed?[FONT=monospace]
[/FONT]```
sudo apt-get install build-essential
```

---

### Post by maustin2 on 2008-11-21
Partyboi2

Yes, I did install build-essential twice

I have read the man page on make several times and tried several options, but no success.

Thanks for the reply.
Still trying.

---

### Post by PmDematagoda on 2008-11-21
Did you try just running:-
```
make
```
?

---

### Post by maustin2 on 2008-11-21
PmDematagoda,

Yes, I have tried just Make,

~/gtk+-2.8.20$ make
make: *** No targets specified and no makefile found.  Stop.

There is are Makefile.msc, .in, .am. These were created after successful run of ./configure. I am following instructions from the Install file, which state to execute ./configure, make and make install.

Thank goodness I strive on challenges.

Thanks for the suggestion.

I can not delete this post.

---

### Post by maustin2 on 2008-11-21
PmDematagoda,

Yes, I have tried just Make,

~/gtk+-2.8.20$ make
make: *** No targets specified and no makefile found.  Stop.

There is are Makefile.msc, .in, .am. These were created after successful run of ./configure. I am following instructions from the Install file, which state to execute ./configure, make and make install.

Thank goodness I strive on challenges.:lolflag:

Thanks for the suggestion.

---

### Post by PmDematagoda on 2008-11-21
Try running:-
```
autoconf
```
in the directory, rerun configure and then try make again.

---

