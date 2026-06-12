---
title: "mediatomb broken after upgrade from 11.04 to 11.10"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by rjesse on 2011-10-22
I just upgraded from 11.04 to 11.10 now mediatomb will not work. I get the following error;

mediatomb: error while loading shared libraries: libavformat.so.52: cannot open shared object file: No such file or directory

Any ideas on how to resolve this?

Rick

---

### Post by masgeeks on 2011-10-22
Have you tried reinstalling mediatomb...???

---

### Post by rjesse on 2011-10-22
I have removed and reinstalled it with apt-get several times

with no luck

I have newer versions of all the libraries in the /usr/lib directory 

I created a soft link via ln -s libavformat.so.53 libavformat.so.52

but it still does not work


Rick

---

### Post by rjesse on 2011-10-22
I think I may have solved it.  It appears that the upgrade now places the mediatomb in /usr/bin as it used to be in /usr/local/bin/.   It was trying to load the binary from /usr/local/bin which appears to be an old version

---

