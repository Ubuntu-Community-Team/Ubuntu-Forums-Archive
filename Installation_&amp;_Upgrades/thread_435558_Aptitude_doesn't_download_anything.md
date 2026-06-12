---
title: "Aptitude doesn't download anything"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by endless_dark on 2007-05-07
Well, since I upgraded to Feisty (I think) my Ubuntu, I realized that I can't install any update or download any package, even I cant apt-get update . This seems to be because connection fails. 
I have my Pc connected to a local network, and the admins blocked most of the ports to avoid people to use p2p programs, but my Apt kept working. Now that I upgraded the connection fails and I think that it's cause the 80 port it's blocked.

Did they change the Apt downloading port in Feisty Fawn? How can I change this? and, if not, Why it's now working so bad? :confused: 

Thanks!
(PD: Sorry for my English, i'm Spanish ;) )

---

### Post by endless_dark on 2007-05-07
Fixed! Today is working! (I don't know what happened)

---

### Post by bapoumba on 2007-05-07
Hi,
as you said, maybe something on their end.
Next time, run:
```
sudo aptitude update
```
and have a look at the error message.

---

