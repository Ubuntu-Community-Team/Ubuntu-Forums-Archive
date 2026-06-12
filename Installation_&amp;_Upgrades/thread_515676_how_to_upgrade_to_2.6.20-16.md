---
title: "how to upgrade to 2.6.20-16?"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by gian on 2007-08-02
Hello,

I have installed a system from 7.04 cd on an HP 7610s notebook, and have X broken.
A web search found that with kernel 2.6.20-16 some issues are solved.

I have already done:
sudo apt-get update && sudo apt-get upgrade
but I still have 2.6.20-15.

How can I upgrade the kernel?

thanks,
regards,
-Gian

---

### Post by Gremlinzzz on 2007-08-02
I just upgraded my kernel and works great so far i did the manually... way.
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
:guitar:

---

### Post by piotrwoj on 2007-08-02
Try to install [SIZE=2]**2.6.20-16**-generic[/SIZE]
[SIZE=2]------------------------------------[/SIZE]
[SIZE=2][Drzwi Antyw&#322;amaniowe]("http://www.drzwi-warszawa.pl/") [/SIZE]
[SIZE=2][Drzwi]("http://www.domar.biz.pl/")[/SIZE]

---

### Post by Seisen on 2007-08-02
What is wrong with X?

---

### Post by gian on 2007-08-02
thank you all for your kind advice.

Updating the kernel fixed the Xserver problem with my Intel X3100 card.

---

### Post by walkerk on 2007-08-02
> **gian said:**
> thank you all for your kind advice.

Updating the kernel fixed the Xserver problem with my Intel X3100 card.

did you upgrade to 2.6.22-9? If so please reply to my thread so others see.. and so others can benefit.. :)

---

### Post by gian on 2007-08-02
Walkerk,

I did follow your thread, but when I removed Gutsy reference from sources.list, and apt-get updated, it downgraded to 2.6.20-16.

Anyway, now my X3100 intel card works...

cheers,
-Gian

---

