---
title: "pppoe and networking"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by zeu on 2005-07-26
i have several problems, for one i can't sudo anythingf because i get this error:

sudo: unable to lookup ariel via getbyhostname()
Password:postdrop: warning: unable to look up public/pickup: no such file or directory.

thats what i get when i try to do sudo pppoeconf.

also, when i go to networking via system > administration menu, it just loads the loading cursor for like 5 seconds, then nothing happens.
nothing loads..

everything else works, the ubuntu install seems to have gone fine, so i dont understand what could be wrong.

thanks in advance.

a little update:
i read this thread:
[http://ubuntuforums.org/showthread.php?t=46532&highlight=gethostbyname](http://ubuntuforums.org/showthread.php?t=46532&highlight=gethostbyname)

but when i type passwd root, or su in console my password doesnt work.
i never set a root password..
how can i fix this?
edit: i cant sett a root password with passwd root because it says that i may not modify or view ionmformation for root.

---

### Post by ubuntp on 2005-07-26
the root password you have to use in sudo is your user password.

---

### Post by zeu on 2005-07-26
[QUOTE=ubuntp]the root password you have to use in sudo is your user password.[/QUOTE]
 ok i fixed everything! im now typing on my ubuntu machne :)

thanks..

---

