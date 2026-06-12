---
title: "Ubuntu (Karmic beta) not recognizing the CD/DVD drive on E6500"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zefew on 2009-10-11
Hi,

I just installed Ubuntu Karmic &#946; on my brand new dell latitude E6500.  The
problem is that Karmic doesn't seem to recognize the cd-rw/dvd drive of my
laptop. (It's a standard drive that comes with the laptop model.)

I know it is indeed working because I installed Ubuntu Karmic with this CD/DVD
ROM in the first place.

I did `dist-upgrade' right after, but no luck.  Worse, `sudo lshw' doesn't say
anything about the CD/DVD rom as well.

In fstab:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


How do I make my Ubuntu recognize the cd/dvd drive?
Any comments are welcome.

---

### Post by zefew on 2009-10-14
bump

---

### Post by rajeev1204 on 2009-10-15
> **zefew said:**
> bump

Can you post the output of dmesg.

---

