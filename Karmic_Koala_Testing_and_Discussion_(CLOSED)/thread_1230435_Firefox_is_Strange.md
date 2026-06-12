---
title: "Firefox is Strange"
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nikolardo on 2009-08-03
I'm running Kubuntu Karmic Koala (but I don't telling anyone I'm running the KKK) and I am having a strange issue with Firefox (3.0.12).
It is unbearably slow, and running it in Konsole gives the following:
"DCOPClient::attachInternal. Attach failed Could not open network socket"
until I run dcopserver, then it works again, all up to speed and such.
Then, it gives
(firefox:5736): Gdk-WARNING **: XID collision, trouble ahead
over and over forever.  It looks bad.  Anyone know what this is all about?
Oh, and I am using this older version of Firefox as 3.5 was being even worse.
Oh, and I'm quite impressed with Karmic so far, only a few glitches apart from this one.

---

### Post by wayne_cat on 2009-08-03
the GTK-Warning is a known problem:

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/401823)

---

### Post by dino99 on 2009-08-03
hi,
install htop & see what apps have the most higher cpu %
If you run FF on an old pc or limited capabilities, you might know that FF need large amount of ram (it's heavy), in that case you can try an other browser like Arora present in the repo (synaptic)

Is it a new installation, does he work normally previously ?, have you this problem since an upgrade ?

---

### Post by nikolardo on 2009-08-03
I had this problem once I started messing around trying to get firefox 3.5.  This was after I upgraded to Karmic, but not immediately after.
Also, just in the system monitor, I can see firefox (when it's unresponsive, before I run dcopserver) is using very little CPU.  It's not unresponsive because it's trying to do a lot of stuff, rather because it's not actually doing anything.

---

