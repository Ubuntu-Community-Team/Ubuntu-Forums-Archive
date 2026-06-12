---
title: "Security: apache php mysql"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by kuckie on 2010-11-30
Hey guys,

I want to install apache, php and mysql on my 10.04 desktop for web development purposes. 

What do I have to pay attention to, in order not to open security holes or make my system vulnerable? 

It is just for developing localy on my machine, there should be absolutely no opening to the internet.

Any help & information appreciated! :)

---

### Post by kuckie on 2010-11-30
I just found this information:

/etc/apache2/ports.conf 

Instead of:
listen 80

Do this:
listen 127.0.0.1:80

Is this enough for security reasons?

---

