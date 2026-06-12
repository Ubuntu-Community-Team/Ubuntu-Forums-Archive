---
title: "Ubuntu 7 Upgrade - Firefox won't load"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by alexjhill on 2007-04-25
Hi guys,

I upgraded from 6.10 to 7.04 and now firefox won't load. I can't see any errors in the logs (not that i really know what i am looking for)


I have removed it from packages menu then re-installed and this has not worked so it's obviously some sort of corrupted preference file but i'm a Linux Newbie and have no idea where to look or start so any help would be great! 

Thanks!

---

### Post by jhnthn on 2007-04-25
Try starting Firefox from a terminal. It might gives you some errors that can help you.

---

### Post by alexjhill on 2007-04-25
hi

I get the following if i type firefox in the terminal window.

alex@Laptop-AH:~$ firefox
Segmentation fault (core dumped)


any ideas?

---

### Post by alexjhill on 2007-04-25
FIxed -


typed:


firefox -safe-mode

had to pick all the reset options and boom - works again!

---

