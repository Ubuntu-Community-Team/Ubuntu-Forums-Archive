---
title: "doing apt-get dist-upgrade?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by ELD on 2006-06-02
Will doing an apt-get dist-upgrade fully update breezy to dapper?

---

### Post by Sarisar on 2006-06-02
Not in itself.  Go into the sources file (can't remember where it is off the top of my head) and change breezy to dapper and then run apt-get update and THEN the upgrade should work.

BUT if you have an nvidia card it will probably break, you need to edit the /etc/X11/xorg.conf file and change nvidia to nv

At least that is how I did it and I just read other posts on the forum, so don't blame me if it's wrong!

---

### Post by ELD on 2006-06-02
Ah i tried it anyway, it broke everything haha.

---

### Post by Sarisar on 2006-06-02
In the words of Bart Simpson.

[QUOTE=Bart Simpson]I didn't do it, nobody saw me, you can't prove anything![/QUOTE]

What exactly did it break?

---

### Post by ELD on 2006-06-02
It gives loads of segmentation fualts and then says the hard drive doesn't exist. Ill just figure out my cd burning problems and a fresh install...

---

