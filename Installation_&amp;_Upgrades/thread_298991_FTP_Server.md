---
title: "FTP Server"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by Kinn on 2006-11-13
I would like to install a FTP server on my kubuntu edgy machine. I looked at the Ubuntu Wiki and it said 

```
sudo apt-get install proftpd
```

would work, but it does not. When I try to install it it checks a few things then returns with the message.

```
E: Couldn't find package proftpd
```

Could anyone recommend a solution?

---

### Post by taurus on 2006-11-13
You need to enable both universe & multiverse in /etc/apt/sources.list.  Open a terminal and edit it by removing the # in front of those lines...  Then update and install it again...

```
sudo nano -Bw /etc/apt/sources.list
sudo aptitude update
sudo aptitude install proftpd
```

---

### Post by Kinn on 2006-11-13
((i accidentally posted this as a topic for some reason..))

what do you mean by "edit the # in front of those line" i'm new, sorry.

---

### Post by Kinn on 2006-11-13
does anyone happen to know what he meant?

---

### Post by taurus on 2006-11-13
> **Kinn said:**
> does anyone happen to know what he meant?
It means remove the # in front of those lines so you can install additional apps like proftpd!!!

---

