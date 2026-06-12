---
title: "new Ubuntu use---a few questions"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by al_ross1 on 2007-01-14
Alright I'm not a total noob I've used Suse for the last couple of years and I've done redhat etc.  I installed 6.10 to try it out and a few things throw me off

1.  How does root login?  I tried and it says the administrator cannot use that login screen
     I need to edit my fstab to make make hda and b partitions work and it won't let me

Plz a little guidance for the new guy

al

---

### Post by ciscosurfer on 2007-01-14
> **al_ross1 said:**
> Alright I'm not a total noob I've used Suse for the last couple of years and I've done redhat etc.  I installed 6.10 to try it out and a few things throw me off

1.  How does root login?  I tried and it says the administrator cannot use that login screen
     I need to edit my fstab to make make hda and b partitions work and it won't let me

Plz a little guidance for the new guy

alLet me be the first to welcome you to Ubuntu Forums!

This wiki link will provide you with the information that you need >> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you have any further questions, please don't hesitate to ask! :-)

---

### Post by al_ross1 on 2007-01-14
thx

---

### Post by Sef on 2007-01-14
To go into fstab, type this in the terminal (Applications > Accessories > Terminal):

```
gksudo gedit /etc/fstab
```

---

