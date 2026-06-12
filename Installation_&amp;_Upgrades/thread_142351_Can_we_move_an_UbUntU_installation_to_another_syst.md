---
title: "Can we move an UbUntU installation to another system"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by sands on 2006-03-10
Hi everyone!!
I want to move my complete linux installation to one of my friends computer..
Something like copying the ext drive contents..and getting linux work on his system..
Is it possible??

---

### Post by nocturn on 2006-03-10
[QUOTE=sands]Hi everyone!!
I want to move my complete linux installation to one of my friends computer..
Something like copying the ext drive contents..and getting linux work on his system..
Is it possible??[/QUOTE]

Yep ;-)

Long answer:
Use either tar with the correct options or something like dd or even Norton Ghost.

---

### Post by ixus_123 on 2006-03-10
is it the same system?  If not you have to consider that it will need different drivers for teh graphics, sound etc


How about backing up your apt to CD-ROM or DVD & taking that, with an Ubuntu install CD over to his/her place.

---

### Post by nocturn on 2006-03-10
[QUOTE=ixus_123]is it the same system?  If not you have to consider that it will need different drivers for teh graphics, sound etc

How about backing up your apt to CD-ROM or DVD & taking that, with an Ubuntu install CD over to his/her place.[/QUOTE]

The drivers are  only a problem for the graphics card becuase Xorg is not very flexible.  The rest is detected at boottime.

I agree with recommending a fresh install though.

---

### Post by frodon on 2006-03-10
You will have a lot of things to reconfigure but yes it's possible.
For me the question is more : will you spend more time installing and configuring a new ubuntu box than reconfigure your ubuntu system on a new hardware ?
I would say that it's faster to perform a fresh install.

---

