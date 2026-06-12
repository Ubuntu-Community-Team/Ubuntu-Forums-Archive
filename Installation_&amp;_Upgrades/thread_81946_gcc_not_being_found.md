---
title: "gcc not being found"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by kulebreeze on 2005-10-25
everytime i tried to compile a programe it alwas say gcc connot be found and its there in /usr/bin/gcc-4.0, what can i do so the compiler can find it?

---

### Post by taurus on 2005-10-25
Could it be that the program you want to compile is looking for gcc while you have /usr/bin/gcc-4.0?  Maybe you want to link it as

sudo ln -s /usr/bin/gcc-4.0 /usr/bin/gcc

---

### Post by withoutclass on 2005-10-25
i was having this problem when using anjuta too, I dont know if that solution works or not, because I'm not using ubuntu ATM due to the shutdown/restart problem with 5.10, but id be interested to see what the problem in fact was

---

