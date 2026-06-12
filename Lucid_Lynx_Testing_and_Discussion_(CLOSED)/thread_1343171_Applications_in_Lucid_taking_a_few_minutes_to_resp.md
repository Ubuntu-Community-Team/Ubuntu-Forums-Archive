---
title: "Applications in Lucid taking a few minutes to respond"
date: 2009-12-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by YosefKaro on 2009-12-01
I just started having this problem right after I experienced a 'Black Screen' where all I could was move my mouse around.  I had to physically shut down my computer.  Being the idiot that I am, I forgot about REISUO and REISUB.  So I did a hard reboot and I think that I have borked my Lucid.  Now it is taking forever for applications to open, then they all open at once.  Any advice?

-Yos

---

### Post by ranch hand on 2009-12-01
Have you just tried to reboot?  I think I would just to see if it helped.  It very well might.

Booting in recovery might be a help too.

---

### Post by zika on 2009-12-01
> **YosefKaro said:**
> I just started having this problem right after I experienced a 'Black Screen' where all I could was move my mouse around.  I had to physically shut down my computer.  Being the idiot that I am, I forgot about REISUO and REISUB.  So I did a hard reboot and I think that I have borked my Lucid.  Now it is taking forever for applications to open, then they all open at once.  Any advice?

-YosIn terminal:```
sudo touch /forcefsck
```and reboot. That will force fsck and Your problem might be solved or exposed ...

---

### Post by ranch hand on 2009-12-01
> **zika said:**
> In terminal:```
sudo touch /forcefsck
```and reboot. That will force fsck and Your problem might be solved or exposed ...
Now there is advice to use a BIG hammer.

As a Blacksmith, I like it.  It should work.  It is a little risky.  I would run it from the Live CD so that it is not working on a mounted FS.

---

### Post by zika on 2009-12-01
> **ranch hand said:**
> Now there is advice to use a BIG hammer.

As a Blacksmith, I like it.  It should work.  It is a little risky.  I would run it from the Live CD so that it is not working on a mounted FS.**No**, it is **not** risky at all. I suggest fsck to be done at boot so the filesystem is **not** mounted yet. It would be risky if I suggested it to be done with mounted file-system. Read carefully, please. No BIG hammer at all. System is checked **this** way every 26 boots or so ...

---

### Post by ranch hand on 2009-12-01
Well whack me with a ruler.  I DO need to learn to read.

---

### Post by Gina on 2009-12-01
I usually run fsck from a Live CD but that'a another way and quicker :)

---

### Post by YosefKaro on 2009-12-02
> **zika said:**
> In terminal:```
sudo touch /forcefsck
```and reboot. That will force fsck and Your problem might be solved or exposed ...


This seems to have helped...thanks a lot.

-Yos

---

