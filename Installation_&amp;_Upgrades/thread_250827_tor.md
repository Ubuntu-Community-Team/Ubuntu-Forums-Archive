---
title: "tor"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by guest5 on 2006-09-04
so the tor isn't up to  date and i understand i need to install it myself.  i am new to linux.  so i ask for help, advice, and direction.  

i have been fortunate enough to not only have most all of my other programs installed, codex, &c, but also to have been pointed in the right direction for this tor install, so here are my thoughts, but are they correct?::

 first, i must modify my /etc/apt/sources.list file
to include the following:

  deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main
  deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main

and only then will the following 'work':

  $ apt-get update
  $ apt-get install tor

am i on the right train of thought here, or???

---

### Post by Iarwain ben-adar on 2006-09-04
Hi,
yeah, that should work for you :D
(btw, it's sudo apt-get)


Iarwain

---

### Post by guest5 on 2006-09-04
thanks and WOW, you all are what?  the word NOTORIOUS comes to mind.  Notorious as to how quick the responces are here.

thanks again, i'll say how it goes.

---

### Post by Iarwain ben-adar on 2006-09-04
No problem :D

btw, that's what makes the difference bewteen this forum, and others :D (if i may say so :D )


Iarwain

---

