---
title: "upgrade from KK to LL: black screen at boot"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by suoko on 2010-02-23
after i upgraded to lucid lynx yesterday on a sony vaio with intel GPU, i ended up with a black screen at boot
fortunately karmic kernel worked so that i could put "nomodeset" in grub line of lucid lynx kernel
it now boots correctly

---

### Post by goebbe on 2010-02-24
I have similar problems. What is your graphic card? 
To find out just open a terminal and type: 
lspci|grep VGA

---

