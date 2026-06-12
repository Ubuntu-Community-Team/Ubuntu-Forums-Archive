---
title: "Ubuntu 9.10 Kernel"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by test.stuff.2009 on 2010-06-04
I installed Ubutnu 9.10 Server on my Dell Server for LAMP & OpenSSH server. After the install was complete, I noticed the the kernel installed on the server was 2.26.31-14-generic instead of 2.26.31-14-server.
 
I am wondering why would generic kernel be installed from ubuntu-server 9.10 cd? And how do go about chaning to server kernel? Or do I even need to do that? Would generic kernel work as server kernel ?
 
Thanx.

---

### Post by wojox on 2010-06-04
Are you sure you installed the Server iso?

I run PAE kernel

```
Linux wojox-server 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux
```

---

### Post by test.stuff.2009 on 2010-06-04
Yes I did install Server ISO.  But It shows the kernel being generic which is used for desktop installation
 
>  
Linux ubuntu 2.6.32-22-generic-pae #35-Ubuntu SMP Tue Jun 1 15:47:31 UTC 2010 i686 GNU/Linux


 
what adavantage does the server kernel have over generic?  I am running LAMP and Openssh Server on this machine.
 
Thanx

---

