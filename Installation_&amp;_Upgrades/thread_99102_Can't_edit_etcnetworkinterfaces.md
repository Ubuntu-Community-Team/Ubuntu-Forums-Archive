---
title: "Can't edit /etc/network/interfaces"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by rpgking on 2005-12-04
I can't edit the /etc/network/interfaces file, since it is read-only for some reason.  I did a server install to try and get xubuntu installed.

I need to modify the interfaces file so that I can configure my wireless card, but I can't even edit the file.  Any help would be greatly appreciated.

---

### Post by aysiu on 2005-12-04
Try this: ```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup
sudo nano /etc/network/interfaces
```

---

### Post by rpgking on 2005-12-04
Whenever I run sudo, I get the following message:

"sudo - unable to lookup host via gethostbyname()"

---

### Post by inhetep on 2005-12-04
Maybe u want to have a look at this

[http://ubuntuforums.org/archive/index.php/t-82900.html](http://ubuntuforums.org/archive/index.php/t-82900.html)

---

### Post by rpgking on 2005-12-04
Yes, I did try editing the file using sudo before.  See my previous message on the error I get.

---

### Post by inhetep on 2005-12-05
Sorry for the missunderstanding it seemed that aysiu and myself  wrote the same thing at the same time. I 've edited the thread, maybe it helps.

---

