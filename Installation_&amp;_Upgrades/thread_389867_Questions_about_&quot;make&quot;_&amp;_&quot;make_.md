---
title: "Questions about &quot;make&quot; &amp; &quot;make install&quot;"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by imatwork on 2007-03-21
Lets assume I'm building source in the following location: /home/user01/prog

When building from source, and running "make", where are the files being 'made' to?
(my guess is somewhere under prog ... ?)

When make finishes, where are files going while running "make install" ?

Can I direct "make install" into creating a .deb file for transport?

NOTE:
Overall, what I'm trying to do, is build a clean production workstation that requires extra softwares that are only available from source. I have an extra 'build' PC that can be cluttered up with programming softwares that will be put back on the shelf as soon as I'm through building source.

Thanks!

---

### Post by imatwork on 2007-03-21
> **imatwork said:**
> Can I direct "make install" into creating a .deb file for transport?


short ANSWER:

01)  sudo apt-get install checkinstall
02)  ./configure
03)  make
04)  sudo checkinstall -D --install=no

---

