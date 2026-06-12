---
title: "Unable to install software through software center"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by ramu123 on 2012-04-23
Hi,

When I tried to install softwares/games through ubuntu software center it's showing following error : 

[CENTER] [IMG]http://i42.tinypic.com/2mez4sm.png[/IMG] [LEFT]
Even though I'm connected to internet!

BTW, I'm able to install softwares through terminal!


[/LEFT]
[/CENTER]

---

### Post by cortman on 2012-04-23
I couldn't see your error, but I assume it was something relating to "unable to connect".
If you ARE able to install via terminal, you best bet is probably just to reinstall the USC.

```
sudo apt-get install --reinstall software-center
```

This is the quickest fix I've found for it yet.

---

### Post by jadtech on 2012-04-23
is that software center or package manager, that is the mesage I been getting from package manager even though it is still updateing and installing updates..

---

### Post by ramu123 on 2012-04-24
> **cortman said:**
> I couldn't see your error, but I assume it was something relating to "unable to connect".
If you ARE able to install via terminal, you best bet is probably just to reinstall the USC.

```
sudo apt-get install --reinstall software-center
```

This is the quickest fix I've found for it yet.
 
It worked! Thanks.

---

### Post by cortman on 2012-04-24
OP, great!
jadtech, please start a new thread on your issue. Thanks!

---

