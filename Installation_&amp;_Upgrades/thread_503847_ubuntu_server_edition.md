---
title: "ubuntu server edition"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by yon2501 on 2007-07-18
ok im new to the whole server technology thing...but yesterday i decided to do something with my old 7year old compac computer it had a 7gb harddrive and 64 megs of ram but i installed a new 160gb harddrive and 512 megs of ram in addition to the 64 megs it already had, i dedided i wanted to turn it into a webserver (i know ill need to get a biger harddrive at some point but i didnt want to spend more then the $150 on it til i actually got it working) i know i have to connect it to my network before i finish installing it but it would be helpful if someone could give me a tutorial on setting up ubuntu server edittion for use as a web server. please help this humble newb =P

---

### Post by bjk03 on 2007-07-18
Here's the guide I used to get 6.06 LTS up and going on a desktop class machine.[http://www.howtoforge.com/node/1388]("http://www.howtoforge.com/node/1388")

---

### Post by az on 2007-07-18
> **yon2501 said:**
> ok im new to the whole server technology thing...but yesterday i decided to do something with my old 7year old compac computer it had a 7gb harddrive and 64 megs of ram but i installed a new 160gb harddrive and 512 megs of ram in addition to the 64 megs it already had, i dedided i wanted to turn it into a webserver (i know ill need to get a biger harddrive at some point but i didnt want to spend more then the $150 on it til i actually got it working) i know i have to connect it to my network before i finish installing it but it would be helpful if someone could give me a tutorial on setting up ubuntu server edittion for use as a web server. please help this humble newb =P

Here:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

No, you will not need a bigger hard drive.  The LAMP stack on top of a base server install takes about 700MB of disk space.   Plus swap, you're looking at more than enough space with your 7 Gig hard drive alone.

---

### Post by az on 2007-07-18
> **bjk03 said:**
> Here's the guide I used to get 6.06 LTS up and going on a desktop class machine.[http://www.howtoforge.com/node/1388]("http://www.howtoforge.com/node/1388")

1.  I would suggest staying away from webmin.  It is horrible and unreliable.  
2.  I would suggest not installing a desktop on a 7 year old machine.

---

