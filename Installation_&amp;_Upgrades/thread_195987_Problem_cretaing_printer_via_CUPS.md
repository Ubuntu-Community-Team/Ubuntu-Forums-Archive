---
title: "Problem cretaing printer via CUPS"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by pelleplutt on 2006-06-13
Hi folks

I´m a newbie who have ran into som problems. Running Drapper server to share my printer and files.
installed a server 6.06 and then installed cups. 

running w3m [http://192.168.1.10:631](http://192.168.1.10:631)
administration
add this printer (finds my usb samsung ml-1610)
pressing add printer (the last step)

then gets message:
426 upgrade required
you must access this page using url [https://ubuntu:631/admin](https://ubuntu:631/admin) (ubuntu is my hostname in my hosts file)

have I missed something when setting up cups?

---

### Post by zxee on 2006-06-13
Did you try to open that url in a browser? It's a local file actually that completes the printer set up. This was the old way some distros like slack set up a printer and I guess it's still the way to configure a print server-if I'm off base here someone correct me please.

---

### Post by l_b on 2006-06-22
I'm having this same problem. Does anyone know an answer to this problem?

---

### Post by EndPerform on 2006-06-24
I got it figured out.  Put the following line in your cupsd.conf:

```
DefaultEncryption IfRequested
```

That will eliminate the 426 error and let you get on with printer configuration.

---

