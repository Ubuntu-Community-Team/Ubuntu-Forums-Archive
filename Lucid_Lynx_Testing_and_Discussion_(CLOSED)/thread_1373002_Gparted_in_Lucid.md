---
title: "Gparted in Lucid?"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Pipps on 2010-01-05
I note that my fresh installation of 10.04 Alpha had not included Gparted.

Is this just an installation anomaly, or is Gparted not expected to be included in Lucid?

---

### Post by yelo3 on 2010-01-05
GParted has never been included by default when you install the distribution on your hard disk. It is only available in the live cd

---

### Post by VMC on 2010-01-05
Easy to install

```
sudo aptitude install gparted
or
sudo apt-get install gparted
```

---

### Post by Pipps on 2010-01-05
I had no idea that Gparted was not usually installed as standard.

Thank you!

---

### Post by ranch hand on 2010-01-05
I have wondered about that but if Ubuntu is the only OS you really do not need gparted, if you do not know what you are doing you can do a lot of damage (take it from me, I learn the hard way), if you know what you are doing it is easy to get and a quick down load, if you only need it very rarely it is on the CD.  This is all I can think of for why it is not there besides needing space on the CD for things like slide shows that are more important.

It gets down loaded at the time of installation on all my installs.

---

### Post by Pipps on 2010-01-05
> **ranch hand said:**
> ...if you do not know what you are doing you can do a lot of damage...

That sounds like me! :rolleyes:

---

### Post by VMC on 2010-01-05
> **ranch hand said:**
> ...if you do not know what you are doing you can do a lot of damage (take it from me, I learn the hard way)..It gets down loaded at the time of installation on all my installs.LOL. This almost sounds like a dichotomy...On the one hand its dangerous, but on the other, let me try it.

---

### Post by Gina on 2010-01-05
I always install GParted because I have several systems installed in umpteen partitions.  I agree with the decision NOT to install it by default - Like Ranch Hand says, it's too dangerous if you don't know what you're doing.  It's very useful to have in the Live CD and I guess that overrides the hazzard for the less experienced user.

---

### Post by ibuclaw on 2010-01-05
Since GParted's main uses for file systems are:
[LIST=1]
[*]Creating
[*]Deleting
[*]Resizing
[*]Integrity Checking
[/LIST]

And with the exception of BtrFS, you can only do these tasks when the file system has been unmounted - hence the LiveCD is a better option to operate it from.

Regards
Iain

---

### Post by ranch hand on 2010-01-06
Gparted is also great for moving partitions from place to place.  Just a copy/paste operation.

This really needs done from another drive, one not involved in the move, or the LiveCD.

---

