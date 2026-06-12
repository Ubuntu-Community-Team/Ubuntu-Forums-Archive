---
title: "this is a bit of a noob question"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by sinrtb on 2010-01-27
I may just not know what it is that i am searching for. 

At most computer labs the one at my old uni particularly had Ubuntu on every PC and a student could log into any of the pc's in the lab and access 'their' desktop. How is this done? are there any examples on the web or here on the Ubuntu site on how to do this?  

Any help would be appreciated.

---

### Post by darkod on 2010-01-27
I'm not sure how it would be called to search for it on google, but in theory, you are probably logging over the network and the actual settings are on a server on the network. Hence, it can load your desktop according to your username on any PC. If your desktop/settings are on your local PC, there is no way to load them on another. It has to be something as described above.

---

### Post by darkod on 2010-01-27
I remembered, they call them roaming profiles. See here:
[http://ubuntuforums.org/showthread.php?t=1085590](http://ubuntuforums.org/showthread.php?t=1085590)

Also you could google for ubuntu roaming profiles, and about NFS mentioned in that link.

---

### Post by velosprinter on 2010-01-27
There are a couple ways. One would be binding to an open directory or Windows AD. This is done using bind9.

They may have also had LTSP 
[http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by sinrtb on 2010-02-20
Thanks for the great starting points!

---

