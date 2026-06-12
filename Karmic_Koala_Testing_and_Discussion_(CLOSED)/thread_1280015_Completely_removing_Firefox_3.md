---
title: "Completely removing Firefox 3"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nutmac on 2009-10-01
I tried removing Firefox 3 by first removing "Firefox Web Browser 3.0" from **Ubuntu Software Center**, followed by removing remaining xulrunner 1.9.0.x and firefox 3.0.x components from **Synaptic Package Manager**. I launch Firefox 3.5 and it insists on leaving "Firefox (en) 3.0.7" and "Xulrunner (en) 1.9.0.8" language translations. I've tried removing them via "sudo firefox" (followed by "sudo chown -R <user_name>:<user_name> ~/.mozilla") but these useless language translations show up eventually regardless.

How I delete them? Thanks.

---

### Post by dt_ on 2009-10-01
I thought Karmic was supposed to ship with Firefox 3.5, not 3.0.. was I mistaken?

---

### Post by nutmac on 2009-10-01
Yes, but I have Firefox 3 from earlier alpha that I wish to get rid of (without clean installing from the beta).

---

### Post by nutmac on 2009-10-07
I guess the issue is fixed now. I've tried sudo firefox trick described in my original post to remove the translations and they are not persisting anymore.

---

### Post by aysiu on 2009-10-07
> **nutmac said:**
> I guess the issue is fixed now. I've tried sudo firefox trick described in my original post to remove the translations and they are not persisting anymore.
The command *sudo firefox* should **never** be run.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by skillllllz on 2009-10-07
> **aysiu said:**
> The command *sudo firefox* should **never** be run.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

+1
I was going to post the very same link.

---

### Post by emarkay on 2009-10-08
OP, mark this thread as solved.  :)

---

