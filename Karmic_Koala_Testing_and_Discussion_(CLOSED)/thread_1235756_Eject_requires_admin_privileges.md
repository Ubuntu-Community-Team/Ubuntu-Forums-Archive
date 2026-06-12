---
title: "Eject requires admin privileges"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oOarthurOo on 2009-08-09
In order to eject a cd-rom I need to type in my password. Workaround for this?

---

### Post by phenest on 2009-08-09
I'm not getting this. I put an Ubuntu Live CD in the drawer and waited for it to mount. I then opened Nautilus > Computer and used eject from the right click context menu. It dismounted and ejected.

---

### Post by phenest on 2009-08-09
I must admit that the eject button on the CD drawer seems to do nothing, and the keyboard shortcut only seems to dismount the CD. But using 'Eject' from the context menu, does work as expected, with no request for privileges.

---

### Post by oOarthurOo on 2009-08-09
can you post what groups your member is a part of?

---

### Post by wayne_cat on 2009-08-09
it works on my system ... my user is member of these groups

```
root@macbook:/var/log/apt# grep rsch /etc/group
adm:x:4:rschmitt,test
dialout:x:20:rschmitt,test
cdrom:x:24:rschmitt,test
audio:x:29:pulse,rschmitt,test
dip:x:30:rschmitt,test
plugdev:x:46:rschmitt,test
lpadmin:x:109:rschmitt
netdev:x:115:rschmitt,test
admin:x:117:rschmitt
rschmitt:x:1000:
sambashare:x:122:rschmitt
pulse:x:119:rschmitt
pulse-access:x:120:rschmitt
root@macbook:/var/log/apt# 
```

---

### Post by gnomeuser on 2009-08-09
this is likely just a matter of the PolicyKit defaults not yet being adjusted, at least I have noticed in a few places that the defaults are very unsuited for a single user desktop. 

Hang in there as the new world order is tweaked to perfection.

---

